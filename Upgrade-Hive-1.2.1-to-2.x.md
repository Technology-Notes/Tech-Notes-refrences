```
= Hive / Tez Upgrade =

Hive 1.2.1 -> Hive 2.1.1
Tez 0.6.2 -> 0.8.4


0. Stop hiveserver2 / metastore

0. mysqlbackup
# mysqldump -u root -p metastore > /tmp/mysql-hive-1.2.1-metastore.sql

1. Hive
$ /usr/lib/hive/bin/schematool -dbType mysql -info

Metastore connection URL:	 jdbc:mysql://localhost:3306/metastore?createDatabaseIfNotExist=true&useUnicode=true&characterEncoding=UTF-8
Metastore Connection Driver :	 com.mysql.jdbc.Driver
Metastore connection User:	 hive
Hive distribution version:	 1.2.0
Metastore schema version:	 1.2.0

-- package upgrade

yum upgrade -y hive-server2 hive-metastore
yum install mysql-connector-java
ln -sf /usr/share/java/mysql-connector-java.jar /usr/lib/hive/lib/

-- schema upgrade
# mysql -uhive -phive metastore < /usr/lib/hive/scripts/metastore/upgrade/mysql/hive-txn-schema-1.3.0.mysql.sql

# /usr/lib/hive/bin/schematool -dbType mysql -upgradeSchemaFrom 1.2.0 -dryRun

# /usr/lib/hive/bin/schematool -dbType mysql -upgradeSchemaFrom 1.2.0 

$ /usr/lib/hive/bin/schematool -dbType mysql -info


2. Tez 

# yum clean all && yum upgrade -y tez

ssh wnode1 'yum clean all && yum upgrade -y tez'
...

# Build tez tar.gz
$ git clone ...
$ cd tez
$ mvn clean package -Dhadoop.version=2.7.1 -DskipTests


# hadoop fs -rmr /apps/tez/*
# cd /usr/lib/tez && tar cvfz tez.tar.gz *
# hadoop fs -put /usr/lib/tez/tez.tar.gz /apps/tez/

----
Apache Slider (0.91)

# build
-- CentOS-7
$ docker run -ti --rm -v `pwd`:/work bigtop/slaves:trunk-centos-7 bash -l
-- CentOS-6
$ docker run -ti --rm -v `pwd`:/work bigtop/slaves:trunk-centos-6 bash -l

# cd /work
# git clone https://github.com/apache/incubator-slider.git -b branches/branch-0.91
# cd in...
# mvn clean install -DskipTests -Prpm
# ls -als slider-assembly/rpm/slider/RPMS/noarch/


# install
yum install slider

* /usr/lib/slider/conf/slider-env.sh

export JAVA_HOME=/usr/java/latest
export HADOOP_CONF_DIR=/etc/hadoop/conf

* /usr/lib/slider/conf/slider-client.xml


2-1. Configurations
-- /etc/hadoop/conf/hadoop-env.sh

-- /etc/tez/conf/tez-site.xml
<property>
<name>tez.lib.uris</name>
<value>${fs.default.name}/apps/tez/tez-0.8.4.tar.gz</value>
</property>

<property>
<name>tez.am.container.idle.release-timeout-min.millis</name>
<value>30000</value>
</property>

<property>
<name>tez.am.container.idle.release-timeout-max.millis</name>
<value>90000</value>
</property>

<!--
<property>
<name>tez.use.cluster.hadoop-libs</name>
<value>true</value>
</property>
-->



-- /etc/hive/conf/hive-site.xml

<!-- ZK -->
<property>
<name>hive.zookeeper.quorum</name>
<value>mnode1,wnode1,wnode2</value>
</property>

<!-- Tez -->
<property>
     <name>hive.execution.engine</name>
     <value>tez</value>
</property>

<property>
     <name>hive.tez.auto.reducer.parallelism</name>
     <value>true</value>
</property>
 
<property>
     <name>hive.server2.tez.sessions.per.default.queue</name>
     <value>1</value>
</property>
 
<property>
     <name>hive.server2.tez.initialize.default.sessions</name>
     <value>true</value>
</property>

<property>
     <name>hive.prewarm.enabled</name>
     <value>true</value>
</property>

<property>
     <name>hive.prewarm.numcontainers</name>
     <value>2</value>
</property>

<property>
     <name>tez.am.container.reuse.enabled</name>
     <value>true</value>
</property>

<property>
      <name>hive.tez.java.opts</name>
      <value>-Xmx5120m</value>
    </property>

<property>
<name>tez.runtime.io.sort.mb</name>
<value>1000</value>
</property>

<!-- LLAP -->
<property>
      <name>hive.execution.mode</name>
      <value>llap</value>
    </property>

<property>
      <name>hive.llap.execution.mode</name>
      <value>all</value>
    </property>
<property>
      <name>hive.llap.daemon.service.hosts</name>
      <value>@hive_llap</value>
    </property>


3. Services

# Restart YARN
Resource manager
Nodemanager

# service hive-metastore start && service hive-server2 start

# llap

# cd /var/lib/hive/
# sudo -u hive hive --service llap --name hive_llap --instances 2 \
--cache 1000m \
--xmx 4000m \
--size 5120m \
--executors 2 \
--loglevel INFO \
--args " -XX:+UseG1GC -XX:+ResizeTLAB -XX:+UseNUMA  -XX:-ResizePLAB"

cd llap....
export PATH=$PATH:/usr/lib/slider/bin
su -s /bin/bash hive -c "./run.sh"


4. Web UI
Web ui for hs2: http://collector:10002

5. 참고 
https://docs.hortonworks.com/HDPDocuments/HDP2/HDP-2.5.3/bk_command-line-installation/content/llap_install_unsecure.html
https://community.hortonworks.com/articles/56636/hive-understanding-concurrent-sessions-queue-alloc.html

```