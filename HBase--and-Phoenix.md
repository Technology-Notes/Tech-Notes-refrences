stats
```
java.lang.RuntimeException: org.apache.phoenix.schema.TableNotFoundException: ERROR 1012 (42M03): Table undefined. tableName=SYSTEM.STATS
	at org.apache.calcite.avatica.jdbc.JdbcMeta.propagate(JdbcMeta.java:651)
	at org.apache.calcite.avatica.jdbc.JdbcMeta.prepareAndExecute(JdbcMeta.java:715)
	at org.apache.calcite.avatica.remote.LocalService.apply(LocalService.java:186)
	at org.apache.calcite.avatica.remote.Service$PrepareAndExecuteRequest.accept(Service.java:868)
	at org.apache.calcite.avatica.remote.Service$PrepareAndExecuteRequest.accept(Service.java:842)
	at org.apache.calcite.avatica.remote.AbstractHandler.apply(AbstractHandler.java:102)
	at org.apache.calcite.avatica.remote.ProtobufHandler.apply(ProtobufHandler.java:38)
	at org.apache.calcite.avatica.server.AvaticaProtobufHandler.handle(AvaticaProtobufHandler.java:68)
	at org.eclipse.jetty.server.handler.HandlerList.handle(HandlerList.java:52)
	at org.eclipse.jetty.server.handler.HandlerWrapper.handle(HandlerWrapper.java:97)
	at org.eclipse.jetty.server.Server.handle(Server.java:497)
	at org.eclipse.jetty.server.HttpChannel.handle(HttpChannel.java:310)
	at org.eclipse.jetty.server.HttpConnection.onFillable(HttpConnection.java:245)
	at org.eclipse.jetty.io.AbstractConnection$2.run(AbstractConnection.java:540)
	at org.eclipse.jetty.util.thread.QueuedThreadPool.runJob(QueuedThreadPool.java:635)
	at org.eclipse.jetty.util.thread.QueuedThreadPool$3.run(QueuedThreadPool.java:555)
	at java.lang.Thread.run(Thread.java:745)
Caused by: org.apache.phoenix.schema.TableNotFoundException: ERROR 1012 (42M03): Table undefined. tableName=SYSTEM.STATS
	at org.apache.phoenix.compile.FromCompiler$BaseColumnResolver.createTableRef(FromCompiler.java:414)
	at org.apache.phoenix.compile.FromCompiler$SingleTableColumnResolver.<init>(FromCompiler.java:285)
	at org.apache.phoenix.compile.FromCompiler.getResolverForQuery(FromCompiler.java:186)
	at org.apache.phoenix.jdbc.PhoenixStatement$ExecutableSelectStatement.compilePlan(PhoenixStatement.java:392)
	at org.apache.phoenix.jdbc.PhoenixStatement$ExecutableSelectStatement.compilePlan(PhoenixStatement.java:373)
	at org.apache.phoenix.jdbc.PhoenixStatement$1.call(PhoenixStatement.java:266)
	at org.apache.phoenix.jdbc.PhoenixStatement$1.call(PhoenixStatement.java:261)
	at org.apache.phoenix.call.CallRunner.run(CallRunner.java:53)
	at org.apache.phoenix.jdbc.PhoenixStatement.executeQuery(PhoenixStatement.java:260)
	at org.apache.phoenix.jdbc.PhoenixStatement.executeQuery(PhoenixStatement.java:1313)
	at org.apache.phoenix.schema.MetaDataClient.updateStatisticsInternal(MetaDataClient.java:919)
	at org.apache.phoenix.schema.MetaDataClient.updateStatistics(MetaDataClient.java:857)
	at org.apache.phoenix.jdbc.PhoenixStatement$ExecutableUpdateStatisticsStatement$1.execute(PhoenixStatement.java:994)
	at org.apache.phoenix.jdbc.PhoenixStatement$2.call(PhoenixStatement.java:338)
	at org.apache.phoenix.jdbc.PhoenixStatement$2.call(PhoenixStatement.java:326)
	at org.apache.phoenix.call.CallRunner.run(CallRunner.java:53)
	at org.apache.phoenix.jdbc.PhoenixStatement.executeMutation(PhoenixStatement.java:325)
	at org.apache.phoenix.jdbc.PhoenixStatement.execute(PhoenixStatement.java:1345)
	at org.apache.calcite.avatica.jdbc.JdbcMeta.prepareAndExecute(JdbcMeta.java:695)
	... 15 more

```
RC2 -> RC3
```
java.lang.RuntimeException: java.sql.SQLException: ERROR 1015 (42J04): Cannot add column to table when the last PK column is of type VARBINARY or ARRAY. columnName=GUIDE_POST_KEY
	at org.apache.calcite.avatica.jdbc.JdbcMeta.openConnection(JdbcMeta.java:585)
	at org.apache.calcite.avatica.remote.LocalService.apply(LocalService.java:263)
	at org.apache.calcite.avatica.remote.Service$OpenConnectionRequest.accept(Service.java:1642)
	at org.apache.calcite.avatica.remote.Service$OpenConnectionRequest.accept(Service.java:1625)
	at org.apache.calcite.avatica.remote.AbstractHandler.apply(AbstractHandler.java:102)
	at org.apache.calcite.avatica.remote.ProtobufHandler.apply(ProtobufHandler.java:38)
	at org.apache.calcite.avatica.server.AvaticaProtobufHandler.handle(AvaticaProtobufHandler.java:68)
	at org.eclipse.jetty.server.handler.HandlerList.handle(HandlerList.java:52)
	at org.eclipse.jetty.server.handler.HandlerWrapper.handle(HandlerWrapper.java:97)
	at org.eclipse.jetty.server.Server.handle(Server.java:497)
	at org.eclipse.jetty.server.HttpChannel.handle(HttpChannel.java:310)
	at org.eclipse.jetty.server.HttpConnection.onFillable(HttpConnection.java:245)
	at org.eclipse.jetty.io.AbstractConnection$2.run(AbstractConnection.java:540)
	at org.eclipse.jetty.util.thread.QueuedThreadPool.runJob(QueuedThreadPool.java:635)
	at org.eclipse.jetty.util.thread.QueuedThreadPool$3.run(QueuedThreadPool.java:555)
	at java.lang.Thread.run(Thread.java:745)
Caused by: java.sql.SQLException: ERROR 1015 (42J04): Cannot add column to table when the last PK column is of type VARBINARY or ARRAY. columnName=GUIDE_POST_KEY
	at org.apache.phoenix.exception.SQLExceptionCode$Factory$1.newException(SQLExceptionCode.java:422)
	at org.apache.phoenix.exception.SQLExceptionInfo.buildException(SQLExceptionInfo.java:145)
	at org.apache.phoenix.schema.MetaDataClient.addColumn(MetaDataClient.java:2625)
	at org.apache.phoenix.jdbc.PhoenixStatement$ExecutableAddColumnStatement$1.execute(PhoenixStatement.java:1021)
	at org.apache.phoenix.jdbc.PhoenixStatement$2.call(PhoenixStatement.java:338)
	at org.apache.phoenix.jdbc.PhoenixStatement$2.call(PhoenixStatement.java:326)
	at org.apache.phoenix.call.CallRunner.run(CallRunner.java:53)
	at org.apache.phoenix.jdbc.PhoenixStatement.executeMutation(PhoenixStatement.java:325)
	at org.apache.phoenix.jdbc.PhoenixStatement.executeUpdate(PhoenixStatement.java:1326)
	at org.apache.phoenix.query.ConnectionQueryServicesImpl.addColumn(ConnectionQueryServicesImpl.java:2214)
	at org.apache.phoenix.query.ConnectionQueryServicesImpl.addColumnsIfNotExists(ConnectionQueryServicesImpl.java:2242)
	at org.apache.phoenix.query.ConnectionQueryServicesImpl.access$500(ConnectionQueryServicesImpl.java:211)
	at org.apache.phoenix.query.ConnectionQueryServicesImpl$13.call(ConnectionQueryServicesImpl.java:2440)
	at org.apache.phoenix.query.ConnectionQueryServicesImpl$13.call(ConnectionQueryServicesImpl.java:2248)
	at org.apache.phoenix.util.PhoenixContextExecutor.call(PhoenixContextExecutor.java:78)
	at org.apache.phoenix.query.ConnectionQueryServicesImpl.init(ConnectionQueryServicesImpl.java:2248)
	at org.apache.phoenix.jdbc.PhoenixDriver.getConnectionQueryServices(PhoenixDriver.java:233)
	at org.apache.phoenix.jdbc.PhoenixEmbeddedDriver.createConnection(PhoenixEmbeddedDriver.java:135)
	at org.apache.phoenix.jdbc.PhoenixDriver.connect(PhoenixDriver.java:202)
	at java.sql.DriverManager.getConnection(DriverManager.java:571)
	at java.sql.DriverManager.getConnection(DriverManager.java:187)
	at org.apache.calcite.avatica.jdbc.JdbcMeta.openConnection(JdbcMeta.java:582)
	... 15 more


```
Failed task, mr syslog:
```
2016-02-26 10:34:12,663 INFO [hconnection-0x1efb7582-shared--pool2-t4] org.apache.hadoop.hbase.client.RpcRetryingCaller: Call exception, tries=13, retries=35, started=213888 ms ago, cancelled=false, msg=row '' on table 'SYSTEM.CATALOG' at region=SYSTEM.CATALOG,,1453257315715.d5e9564b98cf035163a8e4270333e6cf., hostname=fcbigstg05,16020,1456038654966, seqNum=164402
2016-02-26 10:34:39,433 INFO [hconnection-0x1efb7582-shared--pool2-t4] org.apache.hadoop.hbase.client.RpcRetryingCaller: Call exception, tries=14, retries=35, started=240658 ms ago, cancelled=false, msg=row '' on table 'SYSTEM.CATALOG' at region=SYSTEM.CATALOG,,1453257315715.d5e9564b98cf035163a8e4270333e6cf., hostname=fcbigstg05,16020,1456038654966, seqNum=164414
2016-02-26 10:35:06,914 INFO [hconnection-0x1efb7582-shared--pool2-t4] org.apache.hadoop.hbase.client.RpcRetryingCaller: Call exception, tries=15, retries=35, started=268139 ms ago, cancelled=false, msg=row '' on table 'SYSTEM.CATALOG' at region=SYSTEM.CATALOG,,1453257315715.d5e9564b98cf035163a8e4270333e6cf., hostname=fcbigstg05,16020,1456038654966, seqNum=164427
2016-02-26 10:35:44,354 INFO [hconnection-0x1efb7582-shared--pool2-t4] org.apache.hadoop.hbase.client.RpcRetryingCaller: Call exception, tries=16, retries=35, started=305579 ms ago, cancelled=false, msg=row '' on table 'SYSTEM.CATALOG' at region=SYSTEM.CATALOG,,1453257315715.d5e9564b98cf035163a8e4270333e6cf., hostname=fcbigstg05,16020,1456038654966, seqNum=164461
2016-02-26 10:36:10,970 INFO [hconnection-0x1efb7582-shared--pool2-t4] org.apache.hadoop.hbase.client.RpcRetryingCaller: Call exception, tries=17, retries=35, started=332195 ms ago, cancelled=false, msg=row '' on table 'SYSTEM.CATALOG' at region=SYSTEM.CATALOG,,1453257315715.d5e9564b98cf035163a8e4270333e6cf., hostname=fcbigstg05,16020,1456038654966, seqNum=164471
2016-02-26 10:36:37,937 INFO [hconnection-0x1efb7582-shared--pool2-t4] org.apache.hadoop.hbase.client.RpcRetryingCaller: Call exception, tries=18, retries=35, started=359162 ms ago, cancelled=false, msg=row '' on table 'SYSTEM.CATALOG' at region=SYSTEM.CATALOG,,1453257315715.d5e9564b98cf035163a8e4270333e6cf., hostname=fcbigstg05,16020,1456038654966, seqNum=164486
2016-02-26 10:36:58,126 INFO [hconnection-0x1efb7582-shared--pool2-t4] org.apache.hadoop.hbase.client.RpcRetryingCaller: Call exception, tries=19, retries=35, started=379351 ms ago, cancelled=false, msg=row '' on table 'SYSTEM.CATALOG' at region=SYSTEM.CATALOG,,1453257315715.d5e9564b98cf035163a8e4270333e6cf., hostname=fcbigstg05,16020,1456038654966, seqNum=164538
2016-02-26 10:37:22,034 INFO [hconnection-0x1efb7582-shared--pool2-t4] org.apache.hadoop.hbase.client.RpcRetryingCaller: Call exception, tries=20, retries=35, started=403259 ms ago, cancelled=false, msg=row '' on table 'SYSTEM.CATALOG' at region=SYSTEM.CATALOG,,1453257315715.d5e9564b98cf035163a8e4270333e6cf., hostname=fcbigstg05,16020,1456038654966, seqNum=164546
2016-02-26 10:37:53,904 INFO [hconnection-0x1efb7582-shared--pool2-t4] org.apache.hadoop.hbase.client.RpcRetryingCaller: Call exception, tries=21, retries=35, started=435129 ms ago, cancelled=false, msg=row '' on table 'SYSTEM.CATALOG' at region=SYSTEM.CATALOG,,1453257315715.d5e9564b98cf035163a8e4270333e6cf., hostname=fcbigstg05,16020,1456038654966, seqNum=164561
2016-02-26 10:38:41,916 INFO [hconnection-0x1efb7582-shared--pool2-t4] org.apache.hadoop.hbase.client.RpcRetryingCaller: Call exception, tries=22, retries=35, started=483141 ms ago, cancelled=false, msg=row '' on table 'SYSTEM.CATALOG' at region=SYSTEM.CATALOG,,1453257315715.d5e9564b98cf035163a8e4270333e6cf., hostname=fcbigstg05,16020,1456038654966, seqNum=164656
2016-02-26 10:39:09,105 INFO [hconnection-0x1efb7582-shared--pool2-t4] org.apache.hadoop.hbase.client.RpcRetryingCaller: Call exception, tries=23, retries=35, started=510330 ms ago, cancelled=false, msg=row '' on table 'SYSTEM.CATALOG' at region=SYSTEM.CATALOG,,1453257315715.d5e9564b98cf035163a8e4270333e6cf., hostname=fcbigstg05,16020,1456038654966, seqNum=164664
```

Bulkload 4.7.0 rc
```
16/02/22 18:03:45 INFO mapreduce.Job: Task Id : attempt_1456035298774_0066_m_000002_0, Status : FAILED
AttemptID:attempt_1456035298774_0066_m_000002_0 Timed out after 600 secs

16/02/22 18:05:14 INFO mapreduce.LoadIncrementalHFiles: HFile at hdfs://abcd/tmp/74da7ab1-a8ac-4ba8-9d43-0b70f08f8602/AAA.TBL/0/_tmp/_tmp/f305427aa8304cf98355bf01c1edb5ce.top no longer fits inside a single region. Splitting...

```

Hadoop 2.7.1, HBase 1.1.3 & Phoenix 4.7.0
```
# /usr/lib/phoenix/bin/sqlline.py a1,m1,m2
Setting property: [incremental, false]
Setting property: [isolation, TRANSACTION_READ_COMMITTED]
issuing: !connect jdbc:phoenix:fcbiga1,fcbigm1,fcbigm2 none none org.apache.phoenix.jdbc.PhoenixDriver
Connecting to jdbc:phoenix:fcbiga1,fcbigm1,fcbigm2
SLF4J: Class path contains multiple SLF4J bindings.
SLF4J: Found binding in [jar:file:/usr/lib/phoenix/phoenix-4.7.0-HBase-1.1-client.jar!/org/slf4j/impl/StaticLoggerBinder.class]
SLF4J: Found binding in [jar:file:/usr/lib/hadoop/lib/slf4j-log4j12-1.7.10.jar!/org/slf4j/impl/StaticLoggerBinder.class]
SLF4J: See http://www.slf4j.org/codes.html#multiple_bindings for an explanation.
Error: ERROR 103 (08004): Unable to establish connection. (state=08004,code=103)
java.sql.SQLException: ERROR 103 (08004): Unable to establish connection.
	at org.apache.phoenix.exception.SQLExceptionCode$Factory$1.newException(SQLExceptionCode.java:419)
	at org.apache.phoenix.exception.SQLExceptionInfo.buildException(SQLExceptionInfo.java:145)
	at org.apache.phoenix.query.ConnectionQueryServicesImpl.openConnection(ConnectionQueryServicesImpl.java:387)
	at org.apache.phoenix.query.ConnectionQueryServicesImpl.access$300(ConnectionQueryServicesImpl.java:209)
	at org.apache.phoenix.query.ConnectionQueryServicesImpl$13.call(ConnectionQueryServicesImpl.java:2264)
	at org.apache.phoenix.query.ConnectionQueryServicesImpl$13.call(ConnectionQueryServicesImpl.java:2243)
	at org.apache.phoenix.util.PhoenixContextExecutor.call(PhoenixContextExecutor.java:78)
	at org.apache.phoenix.query.ConnectionQueryServicesImpl.init(ConnectionQueryServicesImpl.java:2243)
	at org.apache.phoenix.jdbc.PhoenixDriver.getConnectionQueryServices(PhoenixDriver.java:230)
	at org.apache.phoenix.jdbc.PhoenixEmbeddedDriver.createConnection(PhoenixEmbeddedDriver.java:135)
	at org.apache.phoenix.jdbc.PhoenixDriver.connect(PhoenixDriver.java:201)
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
	at org.apache.phoenix.query.ConnectionQueryServicesImpl.openConnection(ConnectionQueryServicesImpl.java:385)
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
```
# ls -alsR .
.:
합계 131044
    4 drwxr-xr-x  4 root root     4096 2016-02-19 13:51 .
    4 dr-xr-xr-x 47 root root     4096 2016-02-01 15:00 ..
    4 drwxr-xr-x  2 root root     4096 2016-02-21 14:04 bin
    4 drwxr-xr-x  2 root root     4096 2016-02-19 13:51 lib
88880 -rw-r--r--  1 root root 91012325 2016-02-19 11:54 phoenix-4.7.0-HBase-1.1-client.jar
24672 -rw-r--r--  1 root root 25263350 2016-02-19 11:56 phoenix-4.7.0-HBase-1.1-server.jar
 4056 -rw-r--r--  1 root root  4152939 2016-02-19 11:45 phoenix-4.7.0-HBase-1.1-thin-client.jar
    0 lrwxrwxrwx  1 root root       34 2016-02-19 13:51 phoenix-client.jar -> phoenix-4.7.0-HBase-1.1-client.jar
 1632 -rw-r--r--  1 root root  1669198 2016-02-19 11:43 phoenix-core-4.7.0-HBase-1.1-tests.jar
 3540 -rw-r--r--  1 root root  3624168 2016-02-19 11:44 phoenix-core-4.7.0-HBase-1.1.jar
   24 -rw-r--r--  1 root root    23229 2016-02-19 11:44 phoenix-flume-4.7.0-HBase-1.1-tests.jar
   36 -rw-r--r--  1 root root    34801 2016-02-19 11:44 phoenix-flume-4.7.0-HBase-1.1.jar
 4376 -rw-r--r--  1 root root  4478643 2016-02-19 11:46 phoenix-pherf-4.7.0-HBase-1.1-minimal.jar
   60 -rw-r--r--  1 root root    57683 2016-02-19 11:45 phoenix-pherf-4.7.0-HBase-1.1-tests.jar
  156 -rw-r--r--  1 root root   159110 2016-02-19 11:46 phoenix-pherf-4.7.0-HBase-1.1.jar
   44 -rw-r--r--  1 root root    43098 2016-02-19 11:44 phoenix-pig-4.7.0-HBase-1.1-tests.jar
   44 -rw-r--r--  1 root root    41539 2016-02-19 11:44 phoenix-pig-4.7.0-HBase-1.1.jar
 3280 -rw-r--r--  1 root root  3357690 2016-02-19 11:45 phoenix-server-4.7.0-HBase-1.1-runnable.jar
   20 -rw-r--r--  1 root root    19698 2016-02-19 11:45 phoenix-server-4.7.0-HBase-1.1-tests.jar
   20 -rw-r--r--  1 root root    18338 2016-02-19 11:45 phoenix-server-4.7.0-HBase-1.1.jar
    8 -rw-r--r--  1 root root     7136 2016-02-19 11:45 phoenix-server-client-4.7.0-HBase-1.1-tests.jar
   12 -rw-r--r--  1 root root    10448 2016-02-19 11:45 phoenix-server-client-4.7.0-HBase-1.1.jar
    0 lrwxrwxrwx  1 root root       34 2016-02-19 13:51 phoenix-server.jar -> phoenix-4.7.0-HBase-1.1-server.jar
   92 -rw-r--r--  1 root root    91288 2016-02-19 11:46 phoenix-spark-4.7.0-HBase-1.1-tests.jar
   76 -rw-r--r--  1 root root    76885 2016-02-19 11:46 phoenix-spark-4.7.0-HBase-1.1.jar
    0 lrwxrwxrwx  1 root root       39 2016-02-19 13:51 phoenix-thin-client.jar -> phoenix-4.7.0-HBase-1.1-thin-client.jar

./bin:
합계 152
 4 drwxr-xr-x 2 root root  4096 2016-02-21 14:04 .
 4 drwxr-xr-x 4 root root  4096 2016-02-19 13:51 ..
32 -rwxr-xr-x 1 root root 32440 2016-02-19 05:16 daemon.py
 4 -rwxr-xr-x 1 root root  1881 2016-02-19 05:16 end2endTest.py
 4 -rw-r--r-- 1 root root   840 2016-02-19 05:16 hadoop-metrics2-hbase.properties
 4 -rw-r--r-- 1 root root  2271 2016-02-19 05:16 hadoop-metrics2-phoenix.properties
12 -rw-r--r-- 1 root root  9570 2016-02-21 13:43 hbase-site.xml
 4 -rw-r--r-- 1 root root  2584 2016-02-19 05:16 log4j.properties
 8 -rwxr-xr-x 1 root root  5128 2016-02-19 05:16 performance.py
 4 -rwxr-xr-x 1 root root  3249 2016-02-19 05:16 pherf-cluster.py
 4 -rwxr-xr-x 1 root root  2729 2016-02-19 05:16 pherf-standalone.py
12 -rwxr-xr-x 1 root root  9354 2016-02-19 05:16 phoenix_utils.py
 8 -rw-r--r-- 1 root root  5938 2016-02-21 11:42 phoenix_utils.pyc
 4 -rwxr-xr-x 1 root root  2739 2016-02-19 05:16 psql.py
 8 -rwxr-xr-x 1 root root  7866 2016-02-19 05:16 queryserver.py
 4 -rw-r--r-- 1 root root  1820 2016-02-19 05:16 readme.txt
 8 -rwxr-xr-x 1 root root  5369 2016-02-19 05:16 sqlline-thin.py
 4 -rwxr-xr-x 1 root root  3918 2016-02-19 05:16 sqlline.py
 8 -rw-r--r-- 1 root root  6896 2016-02-19 05:16 tephra
 4 -rwxr-xr-x 1 root root  2037 2016-02-19 05:16 tephra-env.sh
 8 -rwxr-xr-x 1 root root  6884 2016-02-19 05:16 traceserver.py

./lib:
합계 10568
   4 drwxr-xr-x 2 root root    4096 2016-02-19 13:51 .
   4 drwxr-xr-x 4 root root    4096 2016-02-19 13:51 ..
1120 -rw-r--r-- 1 root root 1144670 2016-02-15 15:35 antlr-3.5.jar
3232 -rw-r--r-- 1 root root 3306158 2016-02-15 15:47 calcite-avatica-1.6.0.jar
  48 -rw-r--r-- 1 root root   46577 2016-02-15 15:48 calcite-avatica-server-1.6.0.jar
 256 -rw-r--r-- 1 root root  259600 2016-02-15 15:33 commons-codec-1.7.jar
 292 -rw-r--r-- 1 root root  298829 2016-02-15 15:34 commons-configuration-1.6.jar
  36 -rw-r--r-- 1 root root   34827 2016-02-15 15:33 commons-csv-1.0.jar
 184 -rw-r--r-- 1 root root  185140 2016-02-15 15:34 commons-io-2.4.jar
 280 -rw-r--r-- 1 root root  284220 2016-02-15 15:34 commons-lang-2.6.jar
  64 -rw-r--r-- 1 root root   61829 2016-02-15 15:33 commons-logging-1.2.jar
1848 -rw-r--r-- 1 root root 1891110 2016-02-15 15:35 guava-13.0.1.jar
   0 lrwxrwxrwx 1 root root      38 2016-02-19 13:51 hadoop-annotations.jar -> /usr/lib/hadoop/hadoop-annotations.jar
   0 lrwxrwxrwx 1 root root      31 2016-02-19 13:51 hadoop-auth.jar -> /usr/lib/hadoop/hadoop-auth.jar
   0 lrwxrwxrwx 1 root root      33 2016-02-19 13:51 hadoop-common.jar -> /usr/lib/hadoop/hadoop-common.jar
   0 lrwxrwxrwx 1 root root      36 2016-02-19 13:51 hadoop-hdfs.jar -> /usr/lib/hadoop-hdfs/hadoop-hdfs.jar
   0 lrwxrwxrwx 1 root root      57 2016-02-19 13:51 hadoop-mapreduce-client-app.jar -> /usr/lib/hadoop-mapreduce/hadoop-mapreduce-client-app.jar
   4 lrwxrwxrwx 1 root root      60 2016-02-19 13:51 hadoop-mapreduce-client-common.jar -> /usr/lib/hadoop-mapreduce/hadoop-mapreduce-client-common.jar
   0 lrwxrwxrwx 1 root root      58 2016-02-19 13:51 hadoop-mapreduce-client-core.jar -> /usr/lib/hadoop-mapreduce/hadoop-mapreduce-client-core.jar
   4 lrwxrwxrwx 1 root root      63 2016-02-19 13:51 hadoop-mapreduce-client-jobclient.jar -> /usr/lib/hadoop-mapreduce/hadoop-mapreduce-client-jobclient.jar
   4 lrwxrwxrwx 1 root root      61 2016-02-19 13:51 hadoop-mapreduce-client-shuffle.jar -> /usr/lib/hadoop-mapreduce/hadoop-mapreduce-client-shuffle.jar
   0 lrwxrwxrwx 1 root root      40 2016-02-19 13:51 hadoop-yarn-api.jar -> /usr/lib/hadoop-yarn/hadoop-yarn-api.jar
   0 lrwxrwxrwx 1 root root      43 2016-02-19 13:51 hadoop-yarn-client.jar -> /usr/lib/hadoop-yarn/hadoop-yarn-client.jar
   0 lrwxrwxrwx 1 root root      43 2016-02-19 13:51 hadoop-yarn-common.jar -> /usr/lib/hadoop-yarn/hadoop-yarn-common.jar
   0 lrwxrwxrwx 1 root root      50 2016-02-19 13:51 hadoop-yarn-server-common.jar -> /usr/lib/hadoop-yarn/hadoop-yarn-server-common.jar
   0 lrwxrwxrwx 1 root root      36 2016-02-19 13:51 hbase-annotations.jar -> /usr/lib/hbase/hbase-annotations.jar
   0 lrwxrwxrwx 1 root root      31 2016-02-19 13:51 hbase-client.jar -> /usr/lib/hbase/hbase-client.jar
   0 lrwxrwxrwx 1 root root      31 2016-02-19 13:51 hbase-common.jar -> /usr/lib/hbase/hbase-common.jar
   0 lrwxrwxrwx 1 root root      38 2016-02-19 13:51 hbase-hadoop-compat.jar -> /usr/lib/hbase/hbase-hadoop-compat.jar
   0 lrwxrwxrwx 1 root root      27 2016-02-19 13:51 hbase-it.jar -> /usr/lib/hbase/hbase-it.jar
   0 lrwxrwxrwx 1 root root      36 2016-02-01 17:17 hbase-prefix-tree.jar -> /usr/lib/hbase/hbase-prefix-tree.jar
   0 lrwxrwxrwx 1 root root      34 2016-02-19 13:51 hbase-procedure.jar -> /usr/lib/hbase/hbase-procedure.jar
   0 lrwxrwxrwx 1 root root      33 2016-02-19 13:51 hbase-protocol.jar -> /usr/lib/hbase/hbase-protocol.jar
   0 lrwxrwxrwx 1 root root      31 2016-02-19 13:51 hbase-server.jar -> /usr/lib/hbase/hbase-server.jar
 224 -rw-r--r-- 1 root root  228286 2016-02-15 15:35 jackson-core-asl-1.9.2.jar
 748 -rw-r--r-- 1 root root  765648 2016-02-15 15:35 jackson-mapper-asl-1.9.2.jar
 480 -rw-r--r-- 1 root root  489884 2016-02-15 15:33 log4j-1.2.17.jar
1172 -rw-r--r-- 1 root root 1199572 2016-02-15 15:35 netty-3.6.2.Final.jar
 524 -rw-r--r-- 1 root root  533455 2016-02-15 15:35 protobuf-java-2.5.0.jar
  28 -rw-r--r-- 1 root root   25962 2016-02-15 15:35 slf4j-api-1.6.4.jar
  12 -rw-r--r-- 1 root root    8866 2016-02-15 15:37 slf4j-log4j12-1.7.10.jar
   0 lrwxrwxrwx 1 root root      32 2016-02-19 13:51 zookeeper.jar -> /usr/lib/zookeeper/zookeeper.jar
[root@fcbiga1 phoenix]# hbase classpath
/etc/hbase/conf:/usr/java/jdk1.7.0_79/lib/tools.jar:/usr/lib/hbase:/usr/lib/hbase/lib/activation-1.1.jar:/usr/lib/hbase/lib/aopalliance-1.0.jar:/usr/lib/hbase/lib/apacheds-i18n-2.0.0-M15.jar:/usr/lib/hbase/lib/apacheds-kerberos-codec-2.0.0-M15.jar:/usr/lib/hbase/lib/api-asn1-api-1.0.0-M20.jar:/usr/lib/hbase/lib/api-util-1.0.0-M20.jar:/usr/lib/hbase/lib/asm-3.1.jar:/usr/lib/hbase/lib/avro-1.7.4.jar:/usr/lib/hbase/lib/commons-beanutils-1.7.0.jar:/usr/lib/hbase/lib/commons-beanutils-core-1.8.0.jar:/usr/lib/hbase/lib/commons-cli-1.2.jar:/usr/lib/hbase/lib/commons-codec-1.9.jar:/usr/lib/hbase/lib/commons-collections-3.2.2.jar:/usr/lib/hbase/lib/commons-compress-1.4.1.jar:/usr/lib/hbase/lib/commons-configuration-1.6.jar:/usr/lib/hbase/lib/commons-daemon-1.0.13.jar:/usr/lib/hbase/lib/commons-digester-1.8.jar:/usr/lib/hbase/lib/commons-el-1.0.jar:/usr/lib/hbase/lib/commons-httpclient-3.1.jar:/usr/lib/hbase/lib/commons-io-2.4.jar:/usr/lib/hbase/lib/commons-lang-2.6.jar:/usr/lib/hbase/lib/commons-logging-1.2.jar:/usr/lib/hbase/lib/commons-math-2.2.jar:/usr/lib/hbase/lib/commons-math3-3.1.1.jar:/usr/lib/hbase/lib/commons-net-3.1.jar:/usr/lib/hbase/lib/curator-client-2.7.1.jar:/usr/lib/hbase/lib/curator-framework-2.7.1.jar:/usr/lib/hbase/lib/curator-recipes-2.7.1.jar:/usr/lib/hbase/lib/disruptor-3.3.0.jar:/usr/lib/hbase/lib/findbugs-annotations-1.3.9-1.jar:/usr/lib/hbase/lib/gson-2.2.4.jar:/usr/lib/hbase/lib/guava-12.0.1.jar:/usr/lib/hbase/lib/guice-3.0.jar:/usr/lib/hbase/lib/guice-servlet-3.0.jar:/usr/lib/hbase/lib/hadoop-annotations.jar:/usr/lib/hbase/lib/hadoop-auth.jar:/usr/lib/hbase/lib/hadoop-common.jar:/usr/lib/hbase/lib/hadoop-hdfs.jar:/usr/lib/hbase/lib/hadoop-mapreduce-client-app.jar:/usr/lib/hbase/lib/hadoop-mapreduce-client-common.jar:/usr/lib/hbase/lib/hadoop-mapreduce-client-core.jar:/usr/lib/hbase/lib/hadoop-mapreduce-client-jobclient.jar:/usr/lib/hbase/lib/hadoop-mapreduce-client-shuffle.jar:/usr/lib/hbase/lib/hadoop-yarn-api.jar:/usr/lib/hbase/lib/hadoop-yarn-client.jar:/usr/lib/hbase/lib/hadoop-yarn-common.jar:/usr/lib/hbase/lib/hadoop-yarn-server-common.jar:/usr/lib/hbase/lib/hbase-annotations-1.1.3-tests.jar:/usr/lib/hbase/lib/hbase-annotations-1.1.3.jar:/usr/lib/hbase/lib/hbase-client-1.1.3.jar:/usr/lib/hbase/lib/hbase-common-1.1.3-tests.jar:/usr/lib/hbase/lib/hbase-common-1.1.3.jar:/usr/lib/hbase/lib/hbase-examples-1.1.3.jar:/usr/lib/hbase/lib/hbase-hadoop-compat-1.1.3.jar:/usr/lib/hbase/lib/hbase-hadoop2-compat-1.1.3.jar:/usr/lib/hbase/lib/hbase-it-1.1.3-tests.jar:/usr/lib/hbase/lib/hbase-it-1.1.3.jar:/usr/lib/hbase/lib/hbase-prefix-tree-1.1.3.jar:/usr/lib/hbase/lib/hbase-procedure-1.1.3.jar:/usr/lib/hbase/lib/hbase-protocol-1.1.3.jar:/usr/lib/hbase/lib/hbase-resource-bundle-1.1.3.jar:/usr/lib/hbase/lib/hbase-rest-1.1.3.jar:/usr/lib/hbase/lib/hbase-server-1.1.3-tests.jar:/usr/lib/hbase/lib/hbase-server-1.1.3.jar:/usr/lib/hbase/lib/hbase-shell-1.1.3.jar:/usr/lib/hbase/lib/hbase-thrift-1.1.3.jar:/usr/lib/hbase/lib/htrace-core-3.1.0-incubating.jar:/usr/lib/hbase/lib/httpclient-4.2.5.jar:/usr/lib/hbase/lib/httpcore-4.1.3.jar:/usr/lib/hbase/lib/jackson-core-asl-1.9.13.jar:/usr/lib/hbase/lib/jackson-jaxrs-1.9.13.jar:/usr/lib/hbase/lib/jackson-mapper-asl-1.9.13.jar:/usr/lib/hbase/lib/jackson-xc-1.9.13.jar:/usr/lib/hbase/lib/jamon-runtime-2.3.1.jar:/usr/lib/hbase/lib/jasper-compiler-5.5.23.jar:/usr/lib/hbase/lib/jasper-runtime-5.5.23.jar:/usr/lib/hbase/lib/java-xmlbuilder-0.4.jar:/usr/lib/hbase/lib/javax.inject-1.jar:/usr/lib/hbase/lib/jaxb-api-2.2.2.jar:/usr/lib/hbase/lib/jaxb-impl-2.2.3-1.jar:/usr/lib/hbase/lib/jcodings-1.0.8.jar:/usr/lib/hbase/lib/jersey-client-1.9.jar:/usr/lib/hbase/lib/jersey-core-1.9.jar:/usr/lib/hbase/lib/jersey-guice-1.9.jar:/usr/lib/hbase/lib/jersey-json-1.9.jar:/usr/lib/hbase/lib/jersey-server-1.9.jar:/usr/lib/hbase/lib/jets3t-0.9.0.jar:/usr/lib/hbase/lib/jettison-1.3.3.jar:/usr/lib/hbase/lib/jetty-6.1.26.jar:/usr/lib/hbase/lib/jetty-sslengine-6.1.26.jar:/usr/lib/hbase/lib/jetty-util-6.1.26.jar:/usr/lib/hbase/lib/joni-2.1.2.jar:/usr/lib/hbase/lib/jruby-complete-1.6.8.jar:/usr/lib/hbase/lib/jsch-0.1.42.jar:/usr/lib/hbase/lib/jsp-2.1-6.1.14.jar:/usr/lib/hbase/lib/jsp-api-2.1-6.1.14.jar:/usr/lib/hbase/lib/jsr305-1.3.9.jar:/usr/lib/hbase/lib/junit-4.12.jar:/usr/lib/hbase/lib/leveldbjni-all-1.8.jar:/usr/lib/hbase/lib/libthrift-0.9.0.jar:/usr/lib/hbase/lib/log4j-1.2.17.jar:/usr/lib/hbase/lib/metrics-core-2.2.0.jar:/usr/lib/hbase/lib/netty-3.2.4.Final.jar:/usr/lib/hbase/lib/netty-all-4.0.23.Final.jar:/usr/lib/hbase/lib/paranamer-2.3.jar:/usr/lib/hbase/lib/phoenix-server.jar:/usr/lib/hbase/lib/protobuf-java-2.5.0.jar:/usr/lib/hbase/lib/servlet-api-2.5-6.1.14.jar:/usr/lib/hbase/lib/servlet-api-2.5.jar:/usr/lib/hbase/lib/slf4j-api-1.6.1.jar:/usr/lib/hbase/lib/snappy-java-1.0.4.1.jar:/usr/lib/hbase/lib/spymemcached-2.11.6.jar:/usr/lib/hbase/lib/xercesImpl-2.9.1.jar:/usr/lib/hbase/lib/xml-apis-1.3.04.jar:/usr/lib/hbase/lib/xmlenc-0.52.jar:/usr/lib/hbase/lib/xz-1.0.jar:/usr/lib/hbase/lib/zookeeper.jar:/etc/hadoop/conf:/usr/lib/hadoop/lib/*:/usr/lib/hadoop/.//*:/usr/lib/hadoop-hdfs/./:/usr/lib/hadoop-hdfs/lib/*:/usr/lib/hadoop-hdfs/.//*:/usr/lib/hadoop-yarn/lib/*:/usr/lib/hadoop-yarn/.//*:/usr/lib/hadoop-mapreduce/lib/*:/usr/lib/hadoop-mapreduce/.//*::/usr/lib/tez/*:/usr/lib/tez/lib/*:/etc/tez/conf:/etc/hadoop/conf:/*:/lib/*:/usr/lib/zookeeper/*:/usr/lib/zookeeper/lib/*:

```

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


-- bulk load
15/12/21 11:47:40 INFO mapreduce.Job: Task Id : attempt_1450018293185_0952_m_000004_2, Status : FAILED
Error: java.lang.RuntimeException: java.lang.RuntimeException: org.apache.phoenix.schema.TableNotFoundException: ERROR 1012 (42M03): Table undefined. tableName=Q_INL_CHMBR_HISTORY
	at org.apache.phoenix.mapreduce.FormatToKeyValueMapper.map(FormatToKeyValueMapper.java:170)
	at org.apache.phoenix.mapreduce.FormatToKeyValueMapper.map(FormatToKeyValueMapper.java:61)
	at org.apache.hadoop.mapreduce.Mapper.run(Mapper.java:145)
	at org.apache.hadoop.mapred.MapTask.runNewMapper(MapTask.java:787)
	at org.apache.hadoop.mapred.MapTask.run(MapTask.java:341)
	at org.apache.hadoop.mapred.YarnChild$2.run(YarnChild.java:163)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:415)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1671)
	at org.apache.hadoop.mapred.YarnChild.main(YarnChild.java:158)
Caused by: java.lang.RuntimeException: org.apache.phoenix.schema.TableNotFoundException: ERROR 1012 (42M03): Table undefined. tableName=Q_INL_CHMBR_HISTORY
	at com.google.common.base.Throwables.propagate(Throwables.java:156)
	at org.apache.phoenix.mapreduce.FormatToKeyValueMapper$MapperUpsertListener.errorOnRecord(FormatToKeyValueMapper.java:246)
	at org.apache.phoenix.util.csv.CsvUpsertExecutor.execute(CsvUpsertExecutor.java:92)
	at org.apache.phoenix.util.csv.CsvUpsertExecutor.execute(CsvUpsertExecutor.java:44)
	at org.apache.phoenix.util.UpsertExecutor.execute(UpsertExecutor.java:133)
	at org.apache.phoenix.mapreduce.FormatToKeyValueMapper.map(FormatToKeyValueMapper.java:147)
	... 9 more
Caused by: org.apache.phoenix.schema.TableNotFoundException: ERROR 1012 (42M03): Table undefined. tableName=Q_INL_CHMBR_HISTORY
	at org.apache.phoenix.compile.FromCompiler$BaseColumnResolver.createTableRef(FromCompiler.java:436)
	at org.apache.phoenix.compile.FromCompiler$SingleTableColumnResolver.<init>(FromCompiler.java:285)
	at org.apache.phoenix.compile.FromCompiler.getResolverForMutation(FromCompiler.java:249)
	at org.apache.phoenix.compile.UpsertCompiler.compile(UpsertCompiler.java:289)
	at org.apache.phoenix.jdbc.PhoenixStatement$ExecutableUpsertStatement.compilePlan(PhoenixStatement.java:578)
	at org.apache.phoenix.jdbc.PhoenixStatement$ExecutableUpsertStatement.compilePlan(PhoenixStatement.java:566)
	at org.apache.phoenix.jdbc.PhoenixStatement$2.call(PhoenixStatement.java:331)
	at org.apache.phoenix.jdbc.PhoenixStatement$2.call(PhoenixStatement.java:326)
	at org.apache.phoenix.call.CallRunner.run(CallRunner.java:53)
	at org.apache.phoenix.jdbc.PhoenixStatement.executeMutation(PhoenixStatement.java:324)
	at org.apache.phoenix.jdbc.PhoenixStatement.execute(PhoenixStatement.java:245)
	at org.apache.phoenix.jdbc.PhoenixPreparedStatement.execute(PhoenixPreparedStatement.java:172)
	at org.apache.phoenix.jdbc.PhoenixPreparedStatement.execute(PhoenixPreparedStatement.java:177)
	at org.apache.phoenix.util.csv.CsvUpsertExecutor.execute(CsvUpsertExecutor.java:84)
	... 12 more

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