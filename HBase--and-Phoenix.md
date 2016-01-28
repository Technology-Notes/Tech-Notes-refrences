Schema design:
- http://www.slideshare.net/cloudera/5-h-base-schemahbasecon2012
- https://groups.google.com/forum/#!topic/phoenix-hbase-user/obMwuBwF76M

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