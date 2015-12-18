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