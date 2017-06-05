```
2017. 6. 23 / 26-30
```
```
https://www.oreilly.com/ideas/a-tale-of-two-clusters-mesos-and-yarn
https://www.oreilly.com/ideas/questioning-the-lambda-architecture
http://www.datascienceassn.org/sites/default/files/Newly%20Emerging%20Best%20Practices%20for%20Big%20Data%20-%20Ralph%20Kimball.pdf
https://www.ibm.com/developerworks/library/bd-archpatterns1/
https://amplab.cs.berkeley.edu/wp-content/uploads/2011/06/disk-irrelevant_hotos2011.pdf
http://blog.cloudera.com/blog/2014/09/getting-started-with-big-data-architecture/
https://github.com/dvryaboy/idl_storage_guidelines
http://robertgreiner.com/2014/08/cap-theorem-revisited/
http://blog.nahurst.com/visual-guide-to-nosql-systems
http://events.linuxfoundation.org/sites/events/files/slides/PrestoTalk.pdf

http://events.linuxfoundation.org/sites/events/files/slides/Leveraging%20Docker%20for%20Hadoop%20Build%20Automation%20and%20Big%20Data%20Stack%20Provisioning.pdf

https://github.com/rxin/db-readings
https://github.com/t-ivanov/BigDataReading

https://www.linkedin.com/pulse/100-open-source-big-data-architecture-papers-anil-madan

https://www.nextplatform.com/2015/07/03/building-a-better-hadoop-cluster/
http://www.computerworlduk.com/data/enterprises-just-want-simplicity-when-it-comes-their-hadoop-big-data-strategy-3638198/

https://www.slideshare.net/SparkSummit/data-storage-tips-for-optimal-spark-performancevida-ha-databricks?next_slideshow=1
```

# Day 1

0. 빅데이터 아키텍처 설계
- 오버뷰
  * 강의 소개

- '빅데이터 아키텍처'?
  * 빅데이터 아키텍처 설계 개요

- '데이터 애플리케이션'을 위한 소프트웨어 스택
  * 데이터 생성 기술
    * File format & Compression codecs 
      * Text (CSV, TSV, JSON, XML, and etc.)
      * Apache Thrift, Apache Avro, Protocol Buffers
      * Apache Parquet, Apache ORC, Apache CarbonData
  * 데이터 수집 기술
    * Data Integrations (DBs, Files, Streams...)
  * 데이터 저장 기술
    * Apache Hadoop: HDFS
    * Data Stores like BigTable (Apache HBase, Apache Cassandra, Apache Accumulo, Apache Phoenix, ...)
    * OLAP (Druid, Kylin)
  * 데이터 (분산)처리 기술
    * Apache Hadoop: MapReduce, Apache Spark, Apache Flink, Apache Apex
    * SQL on Hadoop (Apache Hive, SparkSQL, Apache HAWK, Presto)
  * 시각화 기술

- 빅데이터 아키텍처 설계 및 구현
  * 레퍼런스 아키텍처
    * 배치 / 실시간 아키텍처
    * 람다 아키텍처
  * Hadoop/Spark 배포판
    * 배포판 비교 및 선택 가이드 (CDH, HDP, PHD, MapR, IOP ...)
  * 인프라스트럭처 중심의 고려사항 
    * 데이터센터, 클라우드, 컨테이너, 베어메탈, 디스크, 스토리지, 네트워크
  * Cluster Management
    * Cluster Automation (Ansible, Chef, Puppet...)
    * YARN vs Mesos
  
- 빅데이터 아키텍처 패턴 & Best Practices
  * 클러스터 워크로드 관리
  * 메타 데이터 관리
  * 압축
  * 보안
  * 캐시
  * '롤아웃' 시스템 아키텍처 및 실행 전략 (Prod, Dev, Test)

--

# Day 5

0. 사례연구 및 토론
- 사례연구1: 온라인 클릭스트림 분석 시스템
- 사례연구2: 센서 데이터 수집/분석 시스템
- 사예연구3: TBD (SKT DSC 사례?) 
- 오픈소스 사례연구1: Apache Bigtop
- 오픈소스 사례연구2: Projects @Apache Incubator
- 토론

1. 빅데이터를 위한 오픈소스 활용 전략
- '사용자/관리자' 입장에서 오픈소스 활용
  * 엔터프라이즈 시스템에 오픈소스 소프트웨어 도입 시 참고사항
- '개발자' 입장에서 오픈소스 참여
  * 오픈소스 프로젝트 기여(참여) 가이드 및 팁
  * [The Apache way](https://www.apache.org/foundation/how-it-works.html)

2. Emerging Trends and Technologies
- Data Infrastructures
  * Cloud & Containers
- Data Analytics

3. Resources
- Books, websites and etc...


----



