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
TODO:
```
1. 신형 SSD 동작 검증
- Sanity check
- 워크로드 선정 후 리포트 작성
- 워크로드? YCSB + RocksDB
- https://www.samsung.com/us/labs/pdfs/collateral/Performance-Benefits-of-Running-RocksDB-on-SSDs_Whitepaper.pdf

2. metatron + all-flash 개념 검증 (PoC)
- Redis? 
- Kafka? https://www.micron.com/about/blog/2017/october/improve-apache-kafka-performance-with-flash-storage
- Kudu? 
- ......

(metatron + NVMe)제품은 내년 출시
- 상반기 2번 진행 전까지 1번 완료
- 상반기 2번 항목에 대한 아이템 1개 선정 후 테스트 완료

```
----

YCSB:
- https://github.com/chinglinwen/ycsb2graph
- https://github.com/ashleyblackmore/ycsb-log-parser
- https://github.com/namaggarwal/ycsb-autograph-generator
- https://github.com/toddlipcon/kudu-ycsb-experiments
- https://github.com/aerospike/aerospike-benchmarks

https://github.com/filebench/filebench

https://github.com/haydenjames/bench-scripts

----
Kafka:
- https://db-blog.web.cern.ch/blog/prasanth-kothuri/2016-10-benchmarking-apache-kafka-openstack-vms
- https://gist.github.com/jkreps/c7ddb4041ef62a900e6c

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

https://d2.naver.com/helloworld/162498