# SSD (SATA, 2019)

## Cache (NVMe)
 * Redis, https://docs.redislabs.com/latest/rs/concepts/memory-architecture/redis-flash/
 * Redis, https://dzone.com/articles/under-the-hood-redis-enterprise-flash-database-arc

## HTAP
 * Presto + Apache Kudu 
   - https://d2.naver.com/helloworld/9099561
 * Presto + Raptor
   - https://www.slideshare.net/shubhamtagra/presto-bangalore-meetup1-presto-raptorola

## NoSQL
  * https://www.micron.com/about/blog/2018/december/how-to-free-your-read-intensive-nosql-workloads-from-legacy-constraints
  * Cassandra, https://medium.com/netflix-techblog/benchmarking-high-performance-i-o-with-ssd-for-cassandra-on-aws-df621335de0b
  * https://www.samsung.com/us/labs/pdfs/collateral/Performance-Benefits-of-Running-RocksDB-on-SSDs_Whitepaper.pdf

## Event Hub for Fast Data 
 * Kafka, Improve Apache Kafka performance with flash storage, https://www.micron.com/about/blog/2017/october/improve-apache-kafka-performance-with-flash-storage
 * Kafka, SSD Benchmarks on Kafka--Mingmin Chen, Uber (2/16/17), https://www.youtube.com/watch?v=q3e5QjTH59o
 * https://www.samsung.com/semiconductor/global.semi.static/Optimizing_Data_Center_Applications_for_Samsung_NVMe_SSD-0.pdf
 * Pulsar @ Yahoo, https://yahooeng.tumblr.com/post/150078336821/open-sourcing-pulsar-pub-sub-messaging-at-scale

## Object/Block/File storage
  * Ceph + SSD, https://www.micron.com/-/media/client/global/documents/products/other-documents/micron_9200_ceph_3,-d-,0_reference_architecture.pdf
  * Alluxio over Ceph, http://alluxio-users.85194.x6.nabble.com/Alluxio-on-Ceph-td2153.html
  * Alluxio, https://www.samsung.com/semiconductor/global.semi.static/Alluxio-plus-NVMe-WP-v6-0.pdf
  * Minio, https://github.com/minio/minio
    - https://blog.minio.io/modern-data-lake-with-minio-part-1-716a49499533
    - https://blog.minio.io/modern-data-lake-with-minio-part-2-f24fb5f82424
    - https://blog.minio.io/building-an-on-premise-ml-ecosystem-with-minio-powered-by-presto-weka-r-and-s3select-feature-fefbbaa87054
    - https://github.com/starburstdata/presto-minio
    - https://www.alluxio.org/docs/1.7/en/Configuring-Alluxio-with-Minio.html
    - https://codz.me/2017/10/12/minio-and-nginx/
    - https://databricks.com/blog/2017/05/31/top-5-reasons-for-choosing-s3-over-hdfs.html

## HDFS
  * https://www.micron.com/~/media/documents/products/technical-marketing-brief/hadoop_273_drives_faster_results_technical-brief.pdf
  * https://www.slideshare.net/Hadoop_Summit/how-to-use-flash-drives-with-apache-hadoop-3x-real-world-use-cases-and-proof-pointsbetter-results-better-economics
  * http://www.memblaze.com/en/uploads/2016/09/141111335641.pdf
----

# 도구

YCSB:
- https://github.com/pingcap/go-ycsb.git
- https://github.com/chinglinwen/ycsb2graph
- https://github.com/ashleyblackmore/ycsb-log-parser
- https://github.com/namaggarwal/ycsb-autograph-generator
- https://github.com/toddlipcon/kudu-ycsb-experiments
- https://github.com/aerospike/aerospike-benchmarks

https://github.com/aerospike/act

https://github.com/filebench/filebench

https://github.com/haydenjames/bench-scripts

https://github.com/earlephilhower/ezfio

----
Kafka:
- https://db-blog.web.cern.ch/blog/prasanth-kothuri/2016-10-benchmarking-apache-kafka-openstack-vms
- https://gist.github.com/ueokande/b96eadd798fff852551b80962862bfb3
----
q, https://github.com/harelba/q

```
$ brew update && brew install q
$ ls -als
total 16
0 drwxr-xr-x   4 ywkim  staff   128  2 22 10:00 .
0 drwxr-xr-x+ 34 ywkim  staff  1088  2 22 10:00 ..
8 -rw-r--r--   1 ywkim  staff  1087  2 22 09:54 test1.csv
8 -rw-r--r--   1 ywkim  staff  1058  2 22 10:00 test2.csv

$ cat *.csv | q -d "," "select avg(c3) from - where c2 = 'Throughput(ops/sec)'"
2705.09038872

```

csvkit
- https://github.com/wireservice/csvkit

pandas
- https://pandas.pydata.org/

chartify:
- https://github.com/spotify/chartify

Jupyter
- https://github.com/youngwookim/my-docker-stacks

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

## Refs.
* http://codecapsule.com/2014/02/12/coding-for-ssds-part-1-introduction-and-table-of-contents/
* https://d2.naver.com/helloworld/162498
* https://support.binarylane.com.au/support/solutions/articles/1000055889-how-to-benchmark-disk-i-o
