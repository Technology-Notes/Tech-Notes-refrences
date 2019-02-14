```
Software stack
Apache Zookeeper 3.4.6
Apache Hadoop 2.8.4
Apache Spark 2.4.0
Apache Avro 1.8.2
Apache Kafka 1.1.0
Kafka Manager 1.3.3.17
Kafka Schema Registry 4.1.2
Schema Registry UI 0.9.4
Apache Zeppelin 0.8.0
Apache HBase 1.4.6
Apache Phoenix 4.14.1-HBase-1.4

Chart:
XChart, https://github.com/knowm/XChart

Tools and libs:
Typesafe Config
dropwizard-metrics (metrics)
JDBI (jdbc)
HikariCP (connection pool)
failsafe (failsafe)
Caffeine (in-memory cache)
```

Kafka:
```
key.serializer = "org.apache.kafka.common.serialization.StringSerializer"
value.serializer = "io.confluent.kafka.serializers.KafkaAvroSerializer"
key.deserializer = "org.apache.kafka.common.serialization.StringDeserializer"
value.deserializer = "io.confluent.kafka.serializers.KafkaAvroDeserializer"

// schema registry
schema.registry.url = "http://10.38.12.235:8081"
specific.avro.reader = "true"
auto.register.schemas = "false"
```

Kafka Streams:
```
default.key.serde = "org.apache.kafka.common.serialization.Serdes.StringSerde"
default.value.serde = "io.confluent.kafka.streams.serdes.avro.SpecificAvroSerde"
```