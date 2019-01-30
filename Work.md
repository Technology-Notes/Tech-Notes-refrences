# PLUTO
 * Kafka consumer/producer config 분리

# SSD (NVMe, 2019)

NVMe SSD 이용한 제품??

## Cache (NVMe)
 * Redis, https://docs.redislabs.com/latest/rs/concepts/memory-architecture/redis-flash/
 * Redis, https://dzone.com/articles/under-the-hood-redis-enterprise-flash-database-arc

## HTAP
 * Apache Kudu
   - https://d2.naver.com/helloworld/9099561
 * Apache HBase / Phoenix

## NoSQL
  * https://www.micron.com/about/blog/2018/december/how-to-free-your-read-intensive-nosql-workloads-from-legacy-constraints
  * Cassandra, https://medium.com/netflix-techblog/benchmarking-high-performance-i-o-with-ssd-for-cassandra-on-aws-df621335de0b

## Event Hub for Fast Data 
 * Kafka, Improve Apache Kafka performance with flash storage, https://www.micron.com/about/blog/2017/october/improve-apache-kafka-performance-with-flash-storage
 * Kafka, SSD Benchmarks on Kafka--Mingmin Chen, Uber (2/16/17), https://www.youtube.com/watch?v=q3e5QjTH59o
 * https://www.samsung.com/semiconductor/global.semi.static/Optimizing_Data_Center_Applications_for_Samsung_NVMe_SSD-0.pdf

## Object storage
  * Ceph
  * Alluxio over Ceph, http://alluxio-users.85194.x6.nabble.com/Alluxio-on-Ceph-td2153.html
  * Alluxio, https://www.samsung.com/semiconductor/global.semi.static/Alluxio-plus-NVMe-WP-v6-0.pdf

----
1. YARN local dir
2. HBase L2 BucketCache
3. HDFS [SSD]

YCSB, Zipfian vs Uniform:
```
In a nutshell, the distribution affects how YCSB reads and scans over the keyspace:

uniform: each row has an equal probability to be read
zipfian: some rows have more probability to be targeted by reads or scans. Those rows are called "hot set" or "hot spot" and represent popular data, for instance popular threads of a forum. You should set it up with: hotspotdatafraction and hotspotopnfraction. See $YCSB_HOME/workloads/workload_template for more details.

```