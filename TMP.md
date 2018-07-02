JDBC Reporter:

1. https://github.com/wso2/carbon-metrics
* https://github.com/wso2/carbon-metrics/blob/master/components/org.wso2.carbon.metrics.jdbc.reporter/src/main/java/org/wso2/carbon/metrics/jdbc/reporter/JdbcReporter.java

2. https://gist.github.com/abhikalitra/1c252dc20684aaf5d353
```

import com.codahale.metrics.*;
import com.codahale.metrics.Timer;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.jdbc.core.BatchPreparedStatementSetter;
import org.springframework.jdbc.core.JdbcTemplate;

import javax.sql.DataSource;
import java.net.InetAddress;
import java.net.UnknownHostException;
import java.sql.PreparedStatement;
import java.sql.SQLException;
import java.util.*;
import java.util.concurrent.TimeUnit;

/**
 * Reporter which stores the metrics in a database.
 */
public class JdbcReporter extends ScheduledReporter {

    private static final Logger LOGGER = LoggerFactory.getLogger(JdbcReporter.class);
    /**
     * Queries to execute
     */
    private static final String INSERT_GAUGE_QUERY = "INSERT INTO METRICS_GAUGE (source, timestamp, name, value) VALUES(?,?,?,?);";
    private static final String INSERT_COUNTER_QUERY = "INSERT INTO METRICS_COUNTER (source, timestamp, name, count) VALUES(?,?,?,?);";
    private static final String INSERT_METER_QUERY = "INSERT INTO METRICS_METER (source,timestamp,name,count,mean_rate,m1_rate,m5_rate,m15_rate, rate_unit) VALUES(?,?,?,?,?,?,?,?,?);";
    private static final String INSERT_HISTOGRAM_QUERY = "INSERT INTO METRICS_HISTOGRAM (source,timestamp,name,count,max,mean,min,stddev,p50,p75,p95,p98,p99,p999) VALUES(?,?,?,?,?,?,?,?,?,?,?,?,?,?);";
    private static final String INSERT_TIMERS_QUERY =    "INSERT INTO METRICS_TIMER (source,timestamp,name,count,max,mean,min,stddev,p50,p75,p95,p98,p99,p999,mean_rate,m1_rate,m5_rate,m15_rate, rate_unit, duration_unit) VALUES(?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?,?);";

    public static Builder forRegistry(MetricRegistry registry) {
        return new Builder(registry);
    }

    public static class Builder {
        private final MetricRegistry registry;
        private TimeUnit rateUnit;
        private TimeUnit durationUnit;
        private Clock clock;
        private MetricFilter filter;

        private Builder(MetricRegistry registry) {
            this.registry = registry;
            this.rateUnit = TimeUnit.SECONDS;
            this.durationUnit = TimeUnit.MILLISECONDS;
            this.clock = Clock.defaultClock();
            this.filter = MetricFilter.ALL;
        }

        public Builder convertRatesTo(TimeUnit rateUnit) {
            this.rateUnit = rateUnit;
            return this;
        }

        /**
         * Convert durations to the given time unit.
         *
         * @param durationUnit a unit of time
         * @return {@code this}
         */
        public Builder convertDurationsTo(TimeUnit durationUnit) {
            this.durationUnit = durationUnit;
            return this;
        }

        public Builder withClock(Clock clock) {
            this.clock = clock;
            return this;
        }

        public Builder filter(MetricFilter filter) {
            this.filter = filter;
            return this;
        }

        public JdbcReporter build(DataSource dataSource) {
            return new JdbcReporter(registry,
                    dataSource,
                    rateUnit,
                    durationUnit,
                    clock,
                    filter);
        }
    }

    private final Clock clock;
    private final JdbcTemplate jdbcTemplate;
    private final String source;

    public JdbcReporter(MetricRegistry registry, DataSource dataSource, TimeUnit rateUnit, TimeUnit durationUnit, Clock clock, MetricFilter filter) {
        super(registry, "jdbc-reporter", filter, rateUnit, durationUnit);
        this.clock = clock;
        this.jdbcTemplate = new JdbcTemplate(dataSource);
        String hostname = "UNKNOWN";
        try {
            hostname = InetAddress.getLocalHost().getCanonicalHostName();
        } catch (UnknownHostException uhe) {
            LOGGER.error("Error determining hostname.", uhe);
        }
        this.source = hostname;
    }

    @Override
    public void report(SortedMap<String, Gauge> gauges,
                       SortedMap<String, Counter> counters,
                       SortedMap<String, Histogram> histograms,
                       SortedMap<String, Meter> meters,
                       SortedMap<String, Timer> timers) {

        final long timestamp = TimeUnit.MILLISECONDS.toSeconds(clock.getTime());
        LOGGER.debug("Writing metrics to database [START ]");


        reportGauges(timestamp, gauges);
        reportCounters(timestamp, counters);
        reportHistograms(timestamp, histograms);
        reportMeters(timestamp, meters);
        reportTimers(timestamp, timers);

        LOGGER.debug("Writing metrics to database [FINISH]");

    }

    private void reportTimers(final long timestamp, final Map<String, Timer> timers) {
        final List<Map.Entry<String, Timer>> entries = new ArrayList<>(timers.entrySet());
        this.jdbcTemplate.batchUpdate(INSERT_TIMERS_QUERY, new BatchPreparedStatementSetter() {
            @Override
            public void setValues(PreparedStatement ps, int i) throws SQLException {
                Map.Entry<String, Timer> entry = entries.get(i);
                Timer timer = entry.getValue();
                Snapshot snapshot = timer.getSnapshot();
                String name = entry.getKey();

                ps.setString(1, source);
                ps.setLong(2, timestamp);
                ps.setString(3, name);
                ps.setLong(4, timer.getCount());
                ps.setDouble(5, convertDuration(snapshot.getMax()));
                ps.setDouble(6, convertDuration(snapshot.getMean()));
                ps.setDouble(7, convertDuration(snapshot.getMin()));
                ps.setDouble(8, convertDuration(snapshot.getStdDev()));
                ps.setDouble(9, convertDuration(snapshot.getMedian()));
                ps.setDouble(10, convertDuration(snapshot.get75thPercentile()));
                ps.setDouble(11, convertDuration(snapshot.get95thPercentile()));
                ps.setDouble(12, convertDuration(snapshot.get98thPercentile()));
                ps.setDouble(13, convertDuration(snapshot.get99thPercentile()));
                ps.setDouble(14, convertDuration(snapshot.get999thPercentile()));
                ps.setDouble(15, convertRate(timer.getMeanRate()));
                ps.setDouble(16, convertRate(timer.getOneMinuteRate()));
                ps.setDouble(17, convertRate(timer.getFiveMinuteRate()));
                ps.setDouble(18, convertRate(timer.getFifteenMinuteRate()));
                ps.setString(19, getRateUnit());
                ps.setString(20, getDurationUnit());
            }

            @Override
            public int getBatchSize() {
                return entries.size();
            }
        });
    }

    private void reportMeters(final long timestamp, final Map<String, Meter> meters) {
        final List<Map.Entry<String, Meter>> entries = new ArrayList<Map.Entry<String, Meter>>(meters.entrySet());
        this.jdbcTemplate.batchUpdate(INSERT_METER_QUERY, new BatchPreparedStatementSetter() {
            @Override
            public void setValues(PreparedStatement ps, int i) throws SQLException {
                Map.Entry<String, Meter> entry = entries.get(i);
                Meter meter = entry.getValue();
                String name = entry.getKey();

                ps.setString(1, source);
                ps.setLong(2, timestamp);
                ps.setString(3, name);
                ps.setLong(4, meter.getCount());
                ps.setDouble(5, convertRate(meter.getMeanRate()));
                ps.setDouble(6, convertRate(meter.getOneMinuteRate()));
                ps.setDouble(7, convertRate(meter.getFiveMinuteRate()));
                ps.setDouble(8, convertRate(meter.getFifteenMinuteRate()));
                ps.setString(9, getRateUnit());
            }

            @Override
            public int getBatchSize() {
                return entries.size();
            }
        });
    }


    private void reportHistograms(final long timestamp, final Map<String, Histogram> histograms) {
        final List<Map.Entry<String, Histogram>> entries = new ArrayList<Map.Entry<String, Histogram>>(histograms.entrySet());
        this.jdbcTemplate.batchUpdate(INSERT_HISTOGRAM_QUERY, new BatchPreparedStatementSetter() {
            @Override
            public void setValues(PreparedStatement ps, int i) throws SQLException {
                Map.Entry<String, Histogram> entry = entries.get(i);
                Histogram histogram = entry.getValue();
                Snapshot snapshot = histogram.getSnapshot();
                String name = entry.getKey();

                ps.setString(1, source);
                ps.setLong(2, timestamp);
                ps.setString(3, name);
                ps.setLong(4, histogram.getCount());
                ps.setDouble(5, snapshot.getMax());
                ps.setDouble(6, snapshot.getMean());
                ps.setDouble(7, snapshot.getMin());
                ps.setDouble(8, snapshot.getStdDev());
                ps.setDouble(9, snapshot.getMedian());
                ps.setDouble(10, snapshot.get75thPercentile());
                ps.setDouble(11, snapshot.get95thPercentile());
                ps.setDouble(12, snapshot.get98thPercentile());
                ps.setDouble(13, snapshot.get99thPercentile());
                ps.setDouble(14, snapshot.get999thPercentile());
            }

            @Override
            public int getBatchSize() {
                return entries.size();
            }
        });
    }

    private void reportCounters(final long timestamp, final Map<String, Counter> counters) {
        final List<Map.Entry<String, Counter>> entries = new ArrayList<Map.Entry<String, Counter>>(counters.entrySet());
        this.jdbcTemplate.batchUpdate(INSERT_COUNTER_QUERY, new BatchPreparedStatementSetter() {
            @Override
            public void setValues(PreparedStatement ps, int i) throws SQLException {
                Map.Entry<String, Counter> entry = entries.get(i);
                Counter counter = entry.getValue();
                String name = entry.getKey();
                ps.setString(1, source);
                ps.setLong(2, timestamp);
                ps.setString(3, name);
                ps.setLong(4, counter.getCount());
            }

            @Override
            public int getBatchSize() {
                return entries.size();
            }
        });
    }

    private void reportGauges(final long timestamp, final Map<String, Gauge> gauges) {
        final List<Map.Entry<String, Gauge>> entries = new ArrayList<Map.Entry<String, Gauge>>(gauges.entrySet());
        this.jdbcTemplate.batchUpdate(INSERT_GAUGE_QUERY, new BatchPreparedStatementSetter() {
            @Override
            public void setValues(PreparedStatement ps, int i) throws SQLException {
                Map.Entry<String, Gauge> entry = entries.get(i);
                Gauge gauge = entry.getValue();
                String name = entry.getKey();
                ps.setString(1, source);
                ps.setLong(2, timestamp);
                ps.setString(3, name);
                ps.setObject(4, gauge.getValue());
            }

            @Override
            public int getBatchSize() {
                return entries.size();
            }
        });
    }

    private String calculateRateUnit(TimeUnit unit) {
        final String s = unit.toString().toLowerCase(Locale.US);
        return s.substring(0, s.length() - 1);
    }

}
```

