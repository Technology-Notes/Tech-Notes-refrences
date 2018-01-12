Spark 2.2.0, HBase 1.2.5 & Phoenix 4.13.1-HBase-1.2

Ref: https://phoenix.apache.org/phoenix_spark.html

{quote}
To ensure that all requisite Phoenix / HBase platform dependencies are available on the classpath for the Spark executors and drivers, set both ‘spark.executor.extraClassPath’ and ‘spark.driver.extraClassPath’ in spark-defaults.conf to include the ‘phoenix-<version>-client.jar’
{quote}

/etc/spark/conf/spark-defaults.conf:
```
spark.executor.extraClassPath    /usr/lib/phoenix/phoenix-client.jar
spark.driver.extraClassPath      /usr/lib/phoenix/phoenix-client.jar

```
또는

spark-shell:
```
$ spark-shell --conf "spark.executor.extraClassPath=/usr/lib/phoenix/phoenix-client.jar" --conf "spark.driver.extraClassPath=/usr/lib/phoenix/phoenix-client.jar"
```

```
val opts = Map(
  "table" -> "WEB_STAT",
  "zkUrl" -> "node1,node2,node3")

val df = spark.read.format("org.apache.phoenix.spark").options(opts).load

df.show
```

spark-shell on YARN:
```
spark-shell --master yarn --conf "spark.executor.extraClassPath=/usr/lib/phoenix/phoenix-client.jar" --conf "spark.driver.extraClassPath=/usr/lib/phoenix/phoenix-client.jar"
```

----

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