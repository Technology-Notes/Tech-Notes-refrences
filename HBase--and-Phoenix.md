Phoenix-Spark
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

```
Error: Task org.apache.phoenix.job.JobManager$InstrumentedJobFutureTask@4dd94a58 rejected from org.apache.phoenix.job.JobManager$1@2f4919b0[Running, pool size = 128, active threads = 128, queued tasks = 4955, completed tasks = 205] (state=08000,code=101)

org.apache.phoenix.exception.PhoenixIOException: Task org.apache.phoenix.job.JobManager$InstrumentedJobFutureTask@4dd94a58 rejected from org.apache.phoenix.job.JobManager$1@2f4919b0[Running, pool size = 128, active threads = 128, queued tasks = 4955, completed tasks = 205]

            at org.apache.phoenix.util.ServerUtil.parseServerException(ServerUtil.java:111)

            at org.apache.phoenix.iterate.BaseResultIterators.getIterators(BaseResultIterators.java:734)

            at org.apache.phoenix.iterate.BaseResultIterators.getIterators(BaseResultIterators.java:638)

            at org.apache.phoenix.iterate.MergeSortResultIterator.getMinHeap(MergeSortResultIterator.java:72)

            at org.apache.phoenix.iterate.MergeSortResultIterator.minIterator(MergeSortResultIterator.java:93)

            at org.apache.phoenix.iterate.MergeSortResultIterator.next(MergeSortResultIterator.java:58)

            at org.apache.phoenix.iterate.MergeSortTopNResultIterator.next(MergeSortTopNResultIterator.java:85)

            at org.apache.phoenix.jdbc.PhoenixResultSet.next(PhoenixResultSet.java:778)

            at sqlline.BufferedRows.<init>(BufferedRows.java:37)

            at sqlline.SqlLine.print(SqlLine.java:1650)

            at sqlline.Commands.execute(Commands.java:833)

            at sqlline.Commands.sql(Commands.java:732)

            at sqlline.SqlLine.dispatch(SqlLine.java:808)

            at sqlline.SqlLine.begin(SqlLine.java:681)

            at sqlline.SqlLine.start(SqlLine.java:398)

            at sqlline.SqlLine.main(SqlLine.java:292)

Caused by: java.util.concurrent.RejectedExecutionException: Task org.apache.phoenix.job.JobManager$InstrumentedJobFutureTask@4dd94a58 rejected from org.apache.phoenix.job.JobManager$1@2f4919b0[Running, pool size = 128, active threads = 128, queued tasks = 4955, completed tasks = 205]

            at org.apache.phoenix.job.JobManager$InstrumentedThreadPoolExecutor$1.rejectedExecution(JobManager.java:244)

            at java.util.concurrent.ThreadPoolExecutor.reject(ThreadPoolExecutor.java:823)

            at java.util.concurrent.ThreadPoolExecutor.execute(ThreadPoolExecutor.java:1369)

            at org.apache.phoenix.job.JobManager$InstrumentedThreadPoolExecutor.execute(JobManager.java:261)

            at java.util.concurrent.AbstractExecutorService.submit(AbstractExecutorService.java:134)

            at org.apache.phoenix.iterate.ParallelIterators.submitWork(ParallelIterators.java:103)

            at org.apache.phoenix.iterate.BaseResultIterators.getIterators(BaseResultIterators.java:668)

            ... 14 more


```
https://community.hortonworks.com/articles/9377/deploying-the-phoenix-query-server-in-production-e.html

PHOENIX-2743 HivePhoenixHandler for big-big join with predicate push down

Hadoop 2.7.1
```
Error: ERROR 103 (08004): Unable to establish connection. (state=08004,code=103)
java.sql.SQLException: ERROR 103 (08004): Unable to establish connection.
	at org.apache.phoenix.exception.SQLExceptionCode$Factory$1.newException(SQLExceptionCode.java:422)
	at org.apache.phoenix.exception.SQLExceptionInfo.buildException(SQLExceptionInfo.java:145)
	at org.apache.phoenix.query.ConnectionQueryServicesImpl.openConnection(ConnectionQueryServicesImpl.java:392)
	at org.apache.phoenix.query.ConnectionQueryServicesImpl.access$300(ConnectionQueryServicesImpl.java:211)
	at org.apache.phoenix.query.ConnectionQueryServicesImpl$13.call(ConnectionQueryServicesImpl.java:2269)
	at org.apache.phoenix.query.ConnectionQueryServicesImpl$13.call(ConnectionQueryServicesImpl.java:2248)
	at org.apache.phoenix.util.PhoenixContextExecutor.call(PhoenixContextExecutor.java:78)
	at org.apache.phoenix.query.ConnectionQueryServicesImpl.init(ConnectionQueryServicesImpl.java:2248)
	at org.apache.phoenix.jdbc.PhoenixDriver.getConnectionQueryServices(PhoenixDriver.java:233)
	at org.apache.phoenix.jdbc.PhoenixEmbeddedDriver.createConnection(PhoenixEmbeddedDriver.java:135)
	at org.apache.phoenix.jdbc.PhoenixDriver.connect(PhoenixDriver.java:202)
	at sqlline.DatabaseConnection.connect(DatabaseConnection.java:157)
	at sqlline.DatabaseConnection.getConnection(DatabaseConnection.java:203)
	at sqlline.Commands.connect(Commands.java:1064)
	at sqlline.Commands.connect(Commands.java:996)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:606)
	at sqlline.ReflectiveCommandHandler.execute(ReflectiveCommandHandler.java:36)
	at sqlline.SqlLine.dispatch(SqlLine.java:804)
	at sqlline.SqlLine.initArgs(SqlLine.java:588)
	at sqlline.SqlLine.begin(SqlLine.java:656)
	at sqlline.SqlLine.start(SqlLine.java:398)
	at sqlline.SqlLine.main(SqlLine.java:292)
Caused by: java.io.IOException: java.lang.reflect.InvocationTargetException
	at org.apache.hadoop.hbase.client.ConnectionFactory.createConnection(ConnectionFactory.java:240)
	at org.apache.hadoop.hbase.client.ConnectionManager.createConnection(ConnectionManager.java:421)
	at org.apache.hadoop.hbase.client.ConnectionManager.createConnectionInternal(ConnectionManager.java:330)
	at org.apache.hadoop.hbase.client.HConnectionManager.createConnection(HConnectionManager.java:144)
	at org.apache.phoenix.query.HConnectionFactory$HConnectionFactoryImpl.createConnection(HConnectionFactory.java:47)
	at org.apache.phoenix.query.ConnectionQueryServicesImpl.openConnection(ConnectionQueryServicesImpl.java:390)
	... 22 more
Caused by: java.lang.reflect.InvocationTargetException
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:526)
	at org.apache.hadoop.hbase.client.ConnectionFactory.createConnection(ConnectionFactory.java:238)
	... 27 more
Caused by: java.lang.NoSuchMethodError: org.apache.hadoop.net.unix.DomainSocketWatcher.<init>(I)V
	at org.apache.hadoop.hdfs.shortcircuit.DfsClientShmManager.<init>(DfsClientShmManager.java:415)
	at org.apache.hadoop.hdfs.shortcircuit.ShortCircuitCache.<init>(ShortCircuitCache.java:379)
	at org.apache.hadoop.hdfs.ClientContext.<init>(ClientContext.java:96)
	at org.apache.hadoop.hdfs.ClientContext.get(ClientContext.java:145)
	at org.apache.hadoop.hdfs.DFSClient.<init>(DFSClient.java:627)
	at org.apache.hadoop.hdfs.DFSClient.<init>(DFSClient.java:547)
	at org.apache.hadoop.hdfs.DistributedFileSystem.initialize(DistributedFileSystem.java:139)
	at org.apache.hadoop.fs.FileSystem.createFileSystem(FileSystem.java:2653)
	at org.apache.hadoop.fs.FileSystem.access$200(FileSystem.java:92)
	at org.apache.hadoop.fs.FileSystem$Cache.getInternal(FileSystem.java:2687)
	at org.apache.hadoop.fs.FileSystem$Cache.get(FileSystem.java:2669)
	at org.apache.hadoop.fs.FileSystem.get(FileSystem.java:371)
	at org.apache.hadoop.fs.Path.getFileSystem(Path.java:295)
	at org.apache.hadoop.hbase.util.DynamicClassLoader.initTempDir(DynamicClassLoader.java:118)
	at org.apache.hadoop.hbase.util.DynamicClassLoader.<init>(DynamicClassLoader.java:98)
	at org.apache.hadoop.hbase.protobuf.ProtobufUtil.<clinit>(ProtobufUtil.java:241)
	at org.apache.hadoop.hbase.ClusterId.parseFrom(ClusterId.java:64)
	at org.apache.hadoop.hbase.zookeeper.ZKClusterId.readClusterIdZNode(ZKClusterId.java:75)
	at org.apache.hadoop.hbase.client.ZooKeeperRegistry.getClusterId(ZooKeeperRegistry.java:105)
	at org.apache.hadoop.hbase.client.ConnectionManager$HConnectionImplementation.retrieveClusterId(ConnectionManager.java:880)
	at org.apache.hadoop.hbase.client.ConnectionManager$HConnectionImplementation.<init>(ConnectionManager.java:636)
	... 32 more
```

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

-- join
Remote driver error: Encountered exception in sub plan [0] execution.
	at org.apache.calcite.avatica.Helper.createException(Helper.java:49)
	at org.apache.calcite.avatica.Helper.createException(Helper.java:41)
	at org.apache.calcite.avatica.AvaticaStatement.executeInternal(AvaticaStatement.java:143)
	at org.apache.calcite.avatica.AvaticaStatement.execute(AvaticaStatement.java:177)
	at sqlline.Commands.execute(Commands.java:822)
	at sqlline.Commands.sql(Commands.java:732)
	at sqlline.SqlLine.dispatch(SqlLine.java:808)
	at sqlline.SqlLine.begin(SqlLine.java:681)
	at sqlline.SqlLine.start(SqlLine.java:398)
	at sqlline.SqlLine.main(SqlLine.java:292)
java.lang.RuntimeException: Encountered exception in sub plan [0] execution.
	at org.apache.calcite.avatica.jdbc.JdbcMeta.propagate(JdbcMeta.java:651)
	at org.apache.calcite.avatica.jdbc.JdbcMeta.prepareAndExecute(JdbcMeta.java:715)
	at org.apache.calcite.avatica.remote.LocalService.apply(LocalService.java:179)
	at org.apache.calcite.avatica.remote.Service$PrepareAndExecuteRequest.accept(Service.java:1049)
	at org.apache.calcite.avatica.remote.Service$PrepareAndExecuteRequest.accept(Service.java:1023)
	at org.apache.calcite.avatica.remote.AbstractHandler.apply(AbstractHandler.java:100)
	at org.apache.calcite.avatica.remote.ProtobufHandler.apply(ProtobufHandler.java:38)
	at org.apache.calcite.avatica.server.AvaticaProtobufHandler.handle(AvaticaProtobufHandler.java:63)
	at org.eclipse.jetty.server.handler.HandlerList.handle(HandlerList.java:52)
	at org.eclipse.jetty.server.handler.HandlerWrapper.handle(HandlerWrapper.java:97)
	at org.eclipse.jetty.server.Server.handle(Server.java:497)
	at org.eclipse.jetty.server.HttpChannel.handle(HttpChannel.java:310)
	at org.eclipse.jetty.server.HttpConnection.onFillable(HttpConnection.java:245)
	at org.eclipse.jetty.io.AbstractConnection$2.run(AbstractConnection.java:540)
	at org.eclipse.jetty.util.thread.QueuedThreadPool.runJob(QueuedThreadPool.java:635)
	at org.eclipse.jetty.util.thread.QueuedThreadPool$3.run(QueuedThreadPool.java:555)
	at java.lang.Thread.run(Thread.java:745)

Apache Phoenix: Transforming HBase into a SQL Database, http://www.slideshare.net/Hadoop_Summit/w-145p230-ataylorv2
Apache Phoenix: Transforming HBase into a SQL Database, http://www.slideshare.net/HBaseCon/ecosystem-session-2-49044349


DROP table failed with exception:

2015-12-18 12:11:52,171 ERROR [B.defaultRpcServer.handler=46,queue=4,port=16020] coprocessor.MetaDataEndpointImpl: dropTable failed
java.lang.ArrayIndexOutOfBoundsException: 20
	at org.apache.phoenix.schema.PTableImpl.init(PTableImpl.java:380)
	at org.apache.phoenix.schema.PTableImpl.<init>(PTableImpl.java:301)
	at org.apache.phoenix.schema.PTableImpl.makePTable(PTableImpl.java:290)
	at org.apache.phoenix.coprocessor.MetaDataEndpointImpl.getTable(MetaDataEndpointImpl.java:844)
	at org.apache.phoenix.coprocessor.MetaDataEndpointImpl.buildTable(MetaDataEndpointImpl.java:472)
	at org.apache.phoenix.coprocessor.MetaDataEndpointImpl.doDropTable(MetaDataEndpointImpl.java:1450)
	at org.apache.phoenix.coprocessor.MetaDataEndpointImpl.dropTable(MetaDataEndpointImpl.java:1403)
	at org.apache.phoenix.coprocessor.generated.MetaDataProtos$MetaDataService.callMethod(MetaDataProtos.java:11629)
	at org.apache.hadoop.hbase.regionserver.HRegion.execService(HRegion.java:7435)
	at org.apache.hadoop.hbase.regionserver.RSRpcServices.execServiceOnRegion(RSRpcServices.java:1875)
	at org.apache.hadoop.hbase.regionserver.RSRpcServices.execService(RSRpcServices.java:1857)
	at org.apache.hadoop.hbase.protobuf.generated.ClientProtos$ClientService$2.callBlockingMethod(ClientProtos.java:32209)
	at org.apache.hadoop.hbase.ipc.RpcServer.call(RpcServer.java:2114)
	at org.apache.hadoop.hbase.ipc.CallRunner.run(CallRunner.java:101)
	at org.apache.hadoop.hbase.ipc.RpcExecutor.consumerLoop(RpcExecutor.java:130)
	at org.apache.hadoop.hbase.ipc.RpcExecutor$1.run(RpcExecutor.java:107)
	at java.lang.Thread.run(Thread.java:745)