Spark 2.1.0, HBase 1.2.4 & Phoenix 4.10.0-HBase-1.2

/etc/spark/conf/spark-defaults.conf:
```
spark.executor.extraClassPath    /usr/lib/phoenix/phoenix-client.jar
spark.driver.extraClassPath      /usr/lib/phoenix/phoenix-client.jar

```

spark-shell:
```
$ spark-shell --master yarn --deploy-mode client

......

val opts = Map(
  "table" -> "TEST.TEST",
  "zkUrl" -> "node1,node2,node3")

val df = spark.read.format("org.apache.phoenix.spark").options(opts).load

df.show
```

STS:
```
$ /usr/lib/spark/bin/beeline -u 'jdbc:hive2://host:port'

>
CREATE TABLE phoenixtbl
USING org.apache.phoenix.spark
OPTIONS (
table "TEST.TEST", 
zkUrl "node1,node2,node3"
);

```