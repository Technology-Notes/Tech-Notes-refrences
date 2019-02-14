Timezone
- https://issues.apache.org/jira/browse/PHOENIX-4822

## Tuning
- SSD & WAL, https://www.cloudera.com/documentation/enterprise/5-8-x/topics/admin_hbase_wal_storage_policy.html
```
<property>
  <name>hbase.wal.storage.policy</name>
  <value>NONE</value>
  <!--<value>ONE_SSD</value>-->
  <!--<value>ALL_SSD</value>-->
</property>
```
- https://www.cloudera.com/documentation/enterprise/5-8-x/topics/admin_hbase_config.html
- https://community.hortonworks.com/articles/184892/tuning-hbase-for-optimized-performance-part-1.html
- https://docs.hortonworks.com/HDPDocuments/HDP3/HDP-3.0.0/hbase-data-access/content/deploying_hbase.html
----

https://www.slideshare.net/mas4share/five-major-tips-to-maximize-performance-on-a-200-sql-hbasephoenix-cluster

## Presto Phoenix plugin
- https://github.com/prestosql/presto/pull/76

## Deployment
- PQS & Haproxy, https://community.hortonworks.com/articles/9377/deploying-the-phoenix-query-server-in-production-e.html
- https://www.percona.com/blog/2014/10/03/haproxy-give-me-some-logs-on-centos-6-5/

## Apache Phoenix

https://medium.com/hashmapinc/3-steps-for-bulk-loading-1m-records-in-20-seconds-into-apache-phoenix-99b77ad87387

### .NET Client for Apache Phoenix
- https://github.com/Azure/hdinsight-phoenix-sharp
### PQS JDBC
- https://github.com/joshelser/phoenix-queryserver-jdbc-client


## Etc.
https://www.slideshare.net/cloudera/h-base-and-accumulo-todd-lipcom-jan-25-2012

https://community.hortonworks.com/questions/87231/reduce-existing-hbase-table-regions.html

https://community.hortonworks.com/questions/59557/hbase-phoenix-query-server-tuning-properties.html

https://github.com/Azure-Samples/hbase-phoenix-connection-pool

https://github.com/Pirionfr/pyPhoenix

Spark & HBase/Phoenix:
- https://community.hortonworks.com/content/supportkb/48988/how-to-run-spark-job-to-interact-with-secured-hbas.html

local index
- http://hadoop-hbase.blogspot.kr/2016/10/experiments-hbase-phoenix-and-sql-at.html

http://www.slideshare.net/uprush/subsecondsqlonhadoopatscale

http://engineering.vcnc.co.kr/2013/04/hbase-configuration/

https://community.hortonworks.com/content/supportkb/49612/what-is-the-recommended-number-of-regions-per-regi.html

Phoenix-Spark
- https://community.hortonworks.com/questions/1942/spark-to-phoenix.html
- https://issues.apache.org/jira/browse/PHOENIX-3311
- PHOENIX-3333

HBase compaction
- https://community.hortonworks.com/articles/52616/hbase-compaction-tuning-tips.html

HBase BucketCache
- http://blog.asquareb.com/blog/2016/03/12/hbase-1-dot-0-offheap-cache-configuration/

PHOENIX-3116
Support incompatible HBase 1.1.5 and HBase 1.2.2

https://www.google.co.kr/url?sa=t&rct=j&q=&esrc=s&source=web&cd=9&cad=rja&uact=8&ved=0ahUKEwjL69jom-PPAhXkxlQKHVdOBH4QFghPMAg&url=http%3A%2F%2Fwww.slideshare.net%2Fvanuganti%2Fhbase-hadoop-hbaseoperationspractices&usg=AFQjCNEawwotCYMS2NvRwr25xtBRurtuNg&sig2=UBCwKeky08lH_k-74RxKlg

https://www.inovex.de/blog/hbase-and-phoenix-on-azure-adventures-in-abstraction/

Phoenix-Hive Integration:
```
-- Hive integration
/etc/hive/conf/hive-env.sh:
# Folder containing extra ibraries required for hive compilation/execution can be controlled by:
export HIVE_AUX_JARS_PATH=/usr/lib/phoenix/phoenix-hive.jar

-- Test

-- Hive Managed
create table test.hive_m_phoenix1 (
scd string,
scddesc string
)
STORED BY 'org.apache.phoenix.hive.PhoenixStorageHandler'
TBLPROPERTIES (
'phoenix.table.name'='test.hive_m_phoenix1',
'phoenix.zookeeper.quorum'='mnode1,wnode1,wnode2',
'phoenix.rowkeys'='scd'
);


-- Hive External
create external table test.hive_e_phoenix1 (
scd string,
scddesc string
)
STORED BY 'org.apache.phoenix.hive.PhoenixStorageHandler'
TBLPROPERTIES (
'phoenix.table.name'='bigstats.bigstats_cd',
'phoenix.zookeeper.quorum'='mnode1,wnode1,wnode2',
'phoenix.rowkeys'='scd'
);
```

https://groups.google.com/forum/#!topic/phoenix-hbase-user/D7Q_ksL49Q8

Slides for "Five major tips to maximize performance on a 200+ SQL HBase/Phoenix cluster" are available at http://www.slideshare.net/mas4share/five-major-tips-to-maximize-performance-on-a-200-sql-hbasephoenix-cluster

Here are the slides for "ACID Transactions in Phoenix" - http://www.slideshare.net/caskdata/acid-transactions-in-apache-phoenix-with-apache-tephra-incubating-by-poorna-chandra

Here is the link for slides of Simplified Reads/Writes in HBase( Or "Dont be a Bytecode Jedi"): https://www.dropbox.com/s/zlj2bulozf5p28b/PhoenixCon-uvls.pptx?dl=0

Column qualifier encoding in Apache Phoenix slides are available at http://www.slideshare.net/SamarthJain23/column-encoding

"Phoenix and eHarmony, a better match" slides are available at 
http://www.slideshare.net/VijaykumarVangapandu/eharmony-phoenix-con-2016

"Phoenix Query Server" slides are available at http://www.slideshare.net/je2451/apache-phoenix-query-server-phoenixcon2016

Phoenix + HBase: An Enterprise Grade Data-Warehouse Appliance for Interactive Analytics?
- https://www.youtube.com/watch?v=BR94YR1GP54



PHOENIX-2743 HivePhoenixHandler for big-big join with predicate push down



.NET driver for Apache Phoenix and Phoenix Query Server, https://github.com/Azure/hdinsight-phoenix-sharp


Phoenix bulkload & fs permission:
- https://issues.apache.org/jira/browse/PHOENIX-976
- -Dfs.permissions.umask-mode=000

Schema design:
- http://www.slideshare.net/cloudera/5-h-base-schemahbasecon2012
- https://groups.google.com/forum/#!topic/phoenix-hbase-user/obMwuBwF76M
- http://0b4af6cdc2f0c5998459-c0245c5c937c5dedcca3f1764ecc9b2f.r43.cf2.rackcdn.com/9353-login1210_khurana.pdf

HBase GC tuning:
- http://blog.cloudera.com/blog/2014/12/tuning-java-garbage-collection-for-hbase/
- https://software.intel.com/en-us/blogs/2014/06/18/part-1-tuning-java-garbage-collection-for-hbase
- http://hadoop-hbase.blogspot.kr/2014/03/hbase-gc-tuning-observations.html
- http://www.slideshare.net/lhofhansl/h-base-tuninghbasecon2015ok


HBase read HA
- http://hortonworks.com/blog/apache-hbase-high-availability-next-level/
- https://docs.hortonworks.com/HDPDocuments/HDP2/HDP-2.3.2/bk_hadoop-ha/content/ch_HA-HBase.html
- https://issues.apache.org/jira/browse/PHOENIX-1683
```
A user can turn on TIMELINE read by two ways:(assuming the related table has enabled region replica already)
1) Through JDBC url string: Append ";Consistency=TIMELINE" into URL string
2) alter session set Consistency = 'timeline'
Using alter session set Consistency = 'strong' to turn timeline read off.
When a user uses explain command, "TIMELINE-CONSISTENCY" will be in the plan output when timeline consistency is enabled.
```
- http://hortonworks.com/blog/introduction-to-hbase-mean-time-to-recover-mttr/



HADOOP_CLASSPATH=/usr/lib/hbase/hbase-protocol.jar:/etc/hbase/conf/ hadoop jar /usr/lib/phoenix/phoenix-client.jar org.apache.phoenix.mapreduce.CsvBulkLoadTool  ${HADOOP_MR_RUNTIME_OPTS}  --schema HYNIX  --table Q_INL_CHMBR_HISTORY  --input /user/hive/warehouse/fdc.db/i_q_inl_chmbr_history/id=20151218000000/*  -d $'\001'

## Presentations
* https://www.slideshare.net/search/slideshow?searchfrom=header&q=hbaseconasia2017&ud=any&ft=all&lang=en&sort=
* hbase & semiconductor application
https://www.slideshare.net/HBaseCon/hareqlhbase?qid=675aae40-9c7f-4d92-b118-d66090d85db0&v=&b=&from_search=19
