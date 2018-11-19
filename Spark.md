Spark best practices and tuning - https://legacy.gitbook.com/book/umbertogriffo/apache-spark-best-practices-and-tuning/details

spark.streaming.concurrentJobs
* http://why-not-learn-something.blogspot.com/2016/06/spark-streaming-performance-tuning-on.html
* https://stackoverflow.com/questions/23528006/how-jobs-are-assigned-to-executors-in-spark-streaming

Spark structured streaming, Kafka and Avro:
* Avro SerDe for Apache Spark structured APIs., https://github.com/AbsaOSS/ABRiS

Spark Streaming:
- https://www.slideshare.net/JoanViladrosaRiera/spark-streaming-kafka-010
- https://www.inovex.de/blog/247-spark-streaming-on-yarn-in-production/
- http://mkuthan.github.io/blog/2016/09/30/spark-streaming-on-yarn/
- https://www.stratio.com/blog/optimizing-spark-streaming-applications-apache-kafka/


spark-shell:
```
$ spark-shell
scala> :load src/WordCount.scala

```

Maven Archetype (for Spark):
- https://github.com/spark-in-action/scala-archetype-sparkinaction
- https://www.luckyryan.com/2013/02/15/create-maven-archetype-from-existing-project/
- http://www.avajava.com/tutorials/lessons/how-do-i-create-an-archetype-that-can-run-on-an-existing-project.html


Unit test
- http://www.jesse-anderson.com/2016/04/unit-testing-spark-with-java/
- https://github.com/bosea/spark-unit-testing
- https://dzone.com/articles/testing-spark-code
- https://stackoverflow.com/questions/44536150/how-do-i-use-spark-testing-base-with-maven

## Spark SQL
Spark 2.2 CBO, https://databricks.com/blog/2017/08/31/cost-based-optimizer-in-apache-spark-2-2.html

STS:
- https://developer.ibm.com/hadoop/2016/08/22/how-to-run-queries-on-spark-sql-using-jdbc-via-thrift-server/


## Spark Streaming

https://www.sigmoid.com/spark-streaming-internals/

Structured Streaming:
- https://databricks.com/blog/2017/01/19/real-time-streaming-etl-structured-streaming-apache-spark-2-1.html
- https://docs.databricks.com/spark/latest/structured-streaming/production.html

http://events.linuxfoundation.org/sites/events/files/slides/ApacheCon%20-%20Starting%20with%20Apache%20Spark%2C%20Best%20Practices.pdf

## Examples

https://sparkour.urizone.net/recipes


# Refs
https://spark-summit.org/east-2017/schedule/

https://developer.ibm.com/hadoop/2016/07/18/troubleshooting-and-tuning-spark-for-heavy-workloads/


https://www.google.co.jp/url?sa=t&rct=j&q=&esrc=s&source=web&cd=9&cad=rja&uact=8&ved=0ahUKEwiT8MCix9zSAhUDrJQKHfctBo4QFghgMAg&url=https%3A%2F%2Fwww.slideshare.net%2Fjcmia1%2Fapache-spark-20-tuning-guide&usg=AFQjCNG5vZtS27oqKzKbwaXae1JDa6MogA

https://github.com/pavloff-de/spark4knime