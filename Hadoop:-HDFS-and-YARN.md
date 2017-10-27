hdfs, data locality 
- https://community.hpe.com/t5/Around-the-Storage-Block/Data-Locality-in-Hadoop-Taking-a-Deep-Dive/ba-p/6969665#.WX6BFdPyhAY
- https://community.hortonworks.com/articles/4698/hps-bdra-what-is-different-from-traditional-hadoop.html

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