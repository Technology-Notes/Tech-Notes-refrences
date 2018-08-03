## Hadoop 3.x
- https://www.slideshare.net/Hadoop_Summit/apache-hadoop-30-community-update-79999467
- Hadoop-2 to Hadoop-3, https://www.slideshare.net/Hadoop_Summit/migrating-your-clusters-and-workloads-from-hadoop-2-to-hadoop-3
- https://hortonworks.com/blog/first-class-support-long-running-services-apache-hadoop-yarn/
```
Hadoop 3.0.3+
- Hive 3.0+
- Tez 0.10.0+
- Spark 2.4.0+ ???(SPARK-23534)
- HBase 2.0.0+ (Hadoop 3.0 + HBase 2.0.0 + Spark 2.3.0 + Phoenix 5.0)

HBase 2.0.1 + Phoenix 5.x -> https://github.com/apache/phoenix/commit/a4f93eb458c516206cc3ed25978fb025d752a2a7
```

## WebHDFS
- WebHDFS & HA, https://issues.cloudera.org/browse/DISTRO-403

##
hdfs-over-ftp

https://github.com/chia7712/hof

```
# cat conf/hdfs-over-ftp.properties 

#uncomment this to run ftp server
port = 2222
data-ports = 2223-2225

#uncomment this to run ssl ftp server
#ssl-port = 2226
#ssl-data-ports = 2227-2229

# hdfs uri
#hdfs-uri = hdfs://localhost:8020
hdfs-uri = hdfs://mnode1:9000

# have to be a user which runs HDFS
# this allows you to start ftp server as a root to use 21 port
# and use hdfs as a superuser
superuser = hdfs

```

```
# cat conf/users.properties 

ftpserver.user.test.userpassword=5f4dcc3b5aa765d61d8327deb882cf99
ftpserver.user.test.homedirectory=/user/test
ftpserver.user.test.enableflag=true
ftpserver.user.test.writepermission=true
ftpserver.user.test.maxloginnumber=0
ftpserver.user.test.maxloginperip=0
ftpserver.user.test.idletime=0
ftpserver.user.test.uploadrate=0
ftpserver.user.test.downloadrate=0
ftpserver.user.test.groups=test,users
```

```
su -s /bin/bash hdfs -c "cd /opt/hof-0.1.1/; bin/hof hof conf/hdfs-over-ftp.properties conf/users.properties"

ps aux | grep hof
````

-- HDFS
```
sudo -u hdfs hdfs dfs -mkdir -p /user/test
sudo -u hdfs hdfs dfs -chown test /user/test
```

-- Test
```
$ ftp ftp://test:password@HOSTNAME:2222
```


## MiniHDFS
* http://www.lopakalogic.com/articles/hadoop-articles/hadoop-testing-with-minicluster/

## TBD

hdfs, data locality, HP moonshot, BDRA
- https://community.hpe.com/t5/Around-the-Storage-Block/Data-Locality-in-Hadoop-Taking-a-Deep-Dive/ba-p/6969665#.WX6BFdPyhAY
- https://community.hortonworks.com/articles/4698/hps-bdra-what-is-different-from-traditional-hadoop.html
- https://www.slideshare.net/profyclub_ru/6-key-trends-in-big-data-and-new-reference-architecture-from-hewlett-packard-enterprise-gilles-noisette
- https://www.youtube.com/watch?v=P5GXf9xU2kk
- https://h20195.www2.hpe.com/V2/GetDocument.aspx?docname=4AA6-8931ENW
- HPE Reference Architecture for migration from a traditional Hadoop architecture to an HPE Workload and Density Optimized solution, https://h20195.www2.hpe.com/V2/GetDocument.aspx?docname=a00027171enw
- https://www.slideshare.net/HadoopSummit/empower-datadriven-organizations
- https://www.bluedata.com/blog/2018/03/hadoop-3-decoupling-hadoop-compute-storage/

webhdfs, curl example:
```
curl -L -i -X PUT -T hs_err_pid103121.log "http://icdasdat07:50075/webhdfs/v1/tmp/2.txt?op=CREATE&namenoderpcaddress=icdas&overwrite=true&permission=777"
````

HDP 2.6 Docs:
- https://docs.hortonworks.com/HDPDocuments/HDP2/HDP-2.6.1/index.html

HDFS & Fuse:
- https://www.cloudera.com/documentation/enterprise/5-8-x/topics/cdh_ig_hdfs_mountable.html

Fair scheduler:
http://blog.cloudera.com/blog/2015/09/untangling-apache-hadoop-yarn-part-1/

http://blog.cloudera.com/blog/2015/10/untangling-apache-hadoop-yarn-part-2/

http://blog.cloudera.com/blog/2016/01/untangling-apache-hadoop-yarn-part-3/

http://blog.cloudera.com/blog/2016/06/untangling-apache-hadoop-yarn-part-4-fair-scheduler-queue-basics/


HDFS iNotify
- https://community.hortonworks.com/questions/57661/hdfs-best-way-to-trigger-execution-at-file-arrival.html

https://developer.ibm.com/hadoop/2017/03/10/yarn-node-labels/

https://issues.apache.org/jira/browse/YARN-3214
https://issues.apache.org/jira/browse/HDFS-7285

```
HADOOP_ROOT_LOGGER=DEBUG,console hadoop fs -ls /
```

Fix 'under replicated blocks', https://community.hortonworks.com/articles/4427/fix-under-replicated-blocks-in-hdfs-manually.html

https://www.datadoghq.com/blog/collecting-hadoop-metrics/

https://github.com/miguel10/YARN-Memory-Calculator

MRUnit
- https://www.infoq.com/articles/HadoopMRUnit
- https://mrunit.apache.org/

https://github.com/tomwhite/hadoop-book/blob/master/ch08-mr-types/src/main/java/WholeFileRecordReader.java
- WholeFileInputFormat.java
- WholeFileRecordReader.java
https://github.com/tomwhite/hadoop-book/tree/master/ch06-mr-dev/src/main/java/v4

http://appsintheopen.com/posts/38-maven-config-for-cloudera-map-reduce-programs

YARN Fair shceduler
- https://discuss.zendesk.com/hc/en-us/articles/201999117-How-to-Configure-YARN-Fair-Scheduler-on-a-PHD-Cluster
- https://amalgjose.com/tag/mapred-job-queue-name/

https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/W265aa64a4f21_43ee_b236_c42a1c875961

http://dewoods.com/blog/hadoop-kerberos-guide

http://hortonworks.com/blog/simplifying-user-logs-management-and-access-in-yarn/

## Pig
Hive 2.0, https://issues.apache.org/jira/browse/PIG-4764

HACT, https://cwiki.apache.org/confluence/display/Hive/HCatalog+LoadStore