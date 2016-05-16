```
Java 8

Apache Hadoop 2.7.1

Apache Zookeeper 3.4.6

Apache Hive 1.2.1

Apache Tez 0.6.2

Apache HBase 1.1.3

Apache Phoenix 4.7.0

Presto 0.147-T

Apache Spark 1.5.2

Apache Sqoop 1.4.6

Apache Flume 1.6.0

Azkaban

Python Modules:
snakebite
azkaban cli
pyhive

TiCAT (이천)

Metatron (개발)

```

```

설치
Apache Hadoop

NameNode?
# yum install hadoop-hdfs-namenode

DataNode?
# yum install hadoop-hdfs-datanode

ResourceManager?
# yum install hadoop-yarn-resourcemanager

NodeManager?
# yum install hadoop-yarn-nodemanager

Apache Hive

Hive Server2
# yum install hive-server2

Apache HBase
1) Master
# yum install hbase-master

2) RegionServer?
# yum install hbase-regionserver

Phoenix
HBase RegionServer?:
$ sudo yum install phoenix

Phoenix Queryserver:
$ sudo yum install phoenix-queryserver

Presto
$ sudo yum install -y jdk1.8.0_66.x86_64
$ sudo yum install presto presto-server presto-cli presto-jdbc

설정
Hadoop:
/etc/hadoop/conf/*

Hive:
/etc/hive/conf/*

HBase:
/etc/hbase/conf/*

Phoenix:
/etc/hbase/conf/hbase-site.xml

Presto:
/etc/presto/*.properties
/etc/presto/catalog/*.properties
/etc/presto/presto-env.sh:

JAVA_HOME=/usr/java/latest
JAVA8_HOME=/usr/java/latest

Service 관리
Hadoop:
service hadoop-hdfs-namenode start|stop|restart
service hadoop-hdfs-datanode start|stop|restart
service hadoop-yarn-resourcemanager start|stop|restart
service hadoop-yarn-resourcemanager start|stop|restart

Presto:
$ sudo service presto-server start|stop|restart
 
HBase:
$ sudo service hbase-master start|stop|restart
$ sudo service hbase-regionserver start|stop|restart

# Phoenix QueryServer 
$ sudo service phoenix-queryserver start|stop|restart

설정파일
/etc/COMPONENT_NAME/conf/*
/etc/defaults/COMPONENT_NAME

Presto
/etc/presto/
/etc/presto/catalog/

로그
/var/log/COMPONENT_NAME/*
e.g.,:
/var/log/hadoop-hdfs/*.log
/var/log/hadoop-yarn/*.log
/var/log/hadoop-mapreduce/*.log

서비스 데이터
/var/lib/COMPONENT_NAME/*

Upgrade
$ sudo yum update hadoop\* 
$ sudo yum update presto*
$ sudo yum update hbase*
$ sudo yum update phoenix*
```

```
Packaging and Smoke tests
​https://github.com/youngwookim/bigtop

Hadoop - 2.7.1, master / 1.1
HBase - 1.1.3, BIGTOP-2077, BIGTOP-2077-T
Phoenix - 4.7.0-HBase-1.1, BIGTOP-2077, BIGTOP-2077-T
Presto - 0.132, BIGTOP-1561, BIGTOP-1561-T
Zookeeper - 3.4.6, master 
Sqoop - 1.4.6, master 
Kafka - 0.8.0.1, master 
Spark - 1.5.2, master / 1.1
Presto
0.147-t, ​https://github.com/youngwookim/presto/tree/0.147-t

Hive JDBC Driver
Hive 1.2.1 + Dynamic Service Discovery

​https://github.com/youngwookim/hive-jdbc-uber-jar/commits/1.2.1-DSD
```