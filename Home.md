pypi 미러 : https://github.com/openstack-infra/pypi-mirror

http://blog.cliffano.com/2014/04/06/human-readable-ansible-playbook-log-output-using-callback-plugin/

http://www.slideshare.net/technmsg/improving-hadoop-performancevialinux

http://www.slideshare.net/ChrisNauroth/hadoop-operations2015hadoopsummitsanjosev5

http://www.dbms2.com/2015/06/08/teradata-will-support-presto/

http://hortonworks.com/blog/new-in-hdp-2-3-enterprise-grade-hdfs-data-at-rest-encryption/

http://blog.cloudera.com/blog/2015/06/architectural-patterns-for-near-real-time-data-processing-with-apache-hadoop/

http://radar.oreilly.com/2014/07/questioning-the-lambda-architecture.html

http://blog.confluent.io/2015/02/25/stream-data-platform-1/

http://stackoverflow.com/questions/28082581/what-is-the-differences-between-apache-spark-and-apache-flink

http://www.lopakalogic.com/articles/hadoop-articles/hive-testing/

HDP Packaging http://ko.hortonworks.com/blog/standards-based-packaging-to-support-rolling-upgrades-in-hdp/

https://spark-summit.org/wp-content/uploads/2013/10/Wendell-Spark-Performance.pdf

http://blog.embian.com/19

https://www.altiscale.com/hadoop-blog/spark-on-hadoop/

http://blog.mikiobraun.de/2014/06/future-big-data-flink-stratosphere.html

http://www.slideshare.net/lhofhansl/h-base-tuninghbasecon2015ok

http://www.mkdocs.org/

https://gist.github.com/bakyeono/868a6278360e1c4f503c

http://blog.cloudera.com/blog/2014/06/how-to-create-an-intellij-idea-project-for-apache-hadoop/

http://www.slideshare.net/sbaltagi/spark-or-hadoop-is-it-an-eitheror-proposition-by-slim-baltagi

http://blog.pivotal.io/pivotal/p-o-v/open-data-platform-initiative-putting-an-end-to-faux-pen-source-apache-hadoop-distributions

http://blog.cloudera.com/blog/2014/10/new-in-cdh-5-2-impala-authentication-with-ldap-and-kerberos/

https://speakerdeck.com/vcnc/deiteo-bunseogeul-wihan-scala

http://prof.ict.ac.cn/BigDataBench/

https://github.com/alanshaw/markdown-pdf

http://www.hammerlab.org/2015/02/27/monitoring-spark-with-graphite-and-grafana/

http://files.meetup.com/18367329/Apache%20Phoenix%20at%20Salesforce%20Platform%20Monitoring.pdf

http://sourceforge.net/projects/sernafree/

http://blog.cloudera.com/blog/2014/05/apache-spark-resource-management-and-yarn-app-models/

http://www.quora.com/What-are-pros-and-cons-of-PostgreSQL-and-MySQL

http://blog.2ndquadrant.com/install_multiple_postgresql_servers_redhat_linux/

https://issues.apache.org/jira/browse/HIVE-8376

http://www.slideshare.net/saintya/building-hadoop-based-big-data-environment-pub?related=1

http://www.slideshare.net/saintya/getting-involved-in-world-class-software-engineering-tips-and-tricks-to-join-apache-open-source-community-pub?next_slideshow=1

http://www.slideshare.net/esammer/from-source-to-solution-building-a-system-for-eventoriented-data

http://hortonworks.com/blog/apache-hbase-high-availability-next-level/

https://www.backblaze.com/blog/best-hard-drive/

http://www.principledtechnologies.com/Red%20Hat/Hadoop_OpenJDK_0414.pdf

http://blog.cloudera.com/blog/2015/01/how-to-deploy-apache-hadoop-clusters-like-a-boss/

http://www.ebaytechblog.com/2015/01/12/hdfs-storage-efficiency-using-tiered-storage/#.VLzCMOqsVHY

http://www.slideshare.net/amarsri/apache-lens-at-hadoop-meetup

https://www.xplenty.com/blog/2014/11/5-hadoop-security-projects/

http://blog.cloudera.com/blog/2014/12/the-impala-cookbook/

http://post.oreilly.com/rd/9z1z5amji7g1ql74s1vl2e6nhgqpjkt5h7k00df55jg

http://blog.cloudera.com/blog/2014/11/flafka-apache-flume-meets-apache-kafka-for-event-processing/?imm_mid=0c884c&cmp=em-strata-na-na-newsltr_20141210

Gobblin, http://engineering.linkedin.com/data-ingestion/gobblin-big-data-ease

Impala, http://pandis.net/resources/cidr15impala.pdf

Questioning the Lambda Architecture http://radar.oreilly.com/2014/07/questioning-the-lambda-architecture.html

Hadoop and DNS http://www.sujee.net/tech/articles/hadoop/hadoop-dns/

Jump to Java https://wikidocs.net/book/31

http://www.rossenstoyanchev.org/write/prog/eclipse/eclipse3.html

http://radar.oreilly.com/2014/07/questioning-the-lambda-architecture.html

http://dev.yorhel.nl/ncdu

Jumbo frame? http://docs.lib.purdue.edu/cgi/viewcontent.cgi?article=2770&context=cstech

Install drest:
```
$ sudo pip install drest
```

Testing the Hadoop RM REST API:
```
>>> import drest
>>> api = drest.API('http://192.168.5.141:8088/ws/v1/')
>>> r = api.make_request('GET', '/cluster/metrics')
>>> r.data
{u'clusterMetrics': {u'totalMB': 32000, u'containersPending': 0, u'unhealthyNodes': 1, u'appsCompleted': 0, u'appsRunning': 0, u'decommissionedNodes': 0, u'lostNodes': 0, u'appsKilled': 0, u'appsPending': 0, u'availableMB': 32000, u'activeNodes': 4, u'totalNodes': 5, u'appsSubmitted': 0, u'reservedMB': 0, u'appsFailed': 0, u'rebootedNodes': 0, u'containersAllocated': 0, u'containersReserved': 0, u'allocatedMB': 0}}
```
https://github.com/datafolklabs/drest


http://www.securityweek.com/big-data-smaller-problems-configuring-kerberos-authentication-hadoop

Scrap your MapReduce! (Or, Introduction to Apache Spark), http://rahulkavale.github.io/blog/2014/11/16/scrap-your-map-reduce/

Some Commonly Used Yarn Memory Settings, http://blogs.msdn.com/b/bigdatasupport/archive/2014/11/11/some-commonly-used-yarn-memory-settings.aspx

SAS is Serial SCSI

SATA is Serial ATA

SFF (Small Form Factor) is 2.5" drives

LFF (Large FF) 3.5" drives