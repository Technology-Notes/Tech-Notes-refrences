https://kafka.apache.org/documentation/

https://community.hortonworks.com/articles/80813/kafka-best-practices-1.html

https://sookocheff.com/post/kafka/kafka-in-a-nutshell/
```
Consumers and Consumer Groups

Consumers read from any single partition, allowing you to scale throughput of message consumption in a similar fashion to message production. Consumers can also be organized into consumer groups for a given topic — each consumer within the group reads from a unique partition and the group as a whole consumes all messages from the entire topic. If you have more consumers than partitions then some consumers will be idle because they have no partitions to read from. If you have more partitions than consumers then consumers will receive messages from multiple partitions. If you have equal numbers of consumers and partitions, each consumer reads messages in order from exactly one partition.
```

Scalability of Kafka Messaging using Consumer Groups, http://blog.cloudera.com/blog/2018/05/scalability-of-kafka-messaging-using-consumer-groups/

## Kafka Consumer client
* https://www.confluent.io/blog/tutorial-getting-started-with-the-new-apache-kafka-0-9-consumer-client/
* Kafka Clients (at-most-once, at-least-once, exactly-once and Avro Client), https://medium.com/@ajmalbabu/kafka-0-9-0-clients-db1f43257d30

## Kafka, Spark, Avro Integration
- http://www.hongyusu.com/amt/spark-streaming-kafka-avro-and-registry.html
- https://github.com/opencore/kafka-spark-avro-example

## Kafka Schema Registry
- https://github.com/confluentinc/schema-registry
- https://github.com/Landoop/schema-registry-ui
- https://dzone.com/articles/kafka-avro-serialization-and-the-schema-registry
- http://cloudurable.com/blog/kafka-avro-schema-registry/index.html
- https://www.confluent.io/blog/put-several-event-types-kafka-topic/
- https://www.ctheu.com/2017/03/02/serializing-data-efficiently-with-apache-avro-and-dealing-with-a-schema-registry/
```
The compatibility checks value is one of the following:

NONE - don’t check for schema compatibility
FORWARD - check to make sure last schema version is forward compatible with new schemas
BACKWARDS (default) - make sure new schema is backwards compatible with latest
FULL - make sure new schema is forwards and backwards compatible from latest to new and from new to latest
```

## Unit Test
- https://github.com/chbatey/kafka-unit
- https://github.com/salesforce/kafka-junit
- https://github.com/Landoop/kafka-testing
- https://gist.github.com/benstopford/49555b2962f93f6d50e3
- https://groups.google.com/forum/#!topic/confluent-platform/oOZ852q8aB4

https://github.com/confluentinc/kafka-streams-examples/blob/4710dbf7017666157ce01de4108b57da41399c28/src/test/java/io/confluent/examples/streams/kafka/EmbeddedSingleNodeKafkaCluster.java

```
<dependency>
			<groupId>io.confluent</groupId>
			<artifactId>kafka-streams-examples</artifactId>
			<version>4.1.0</version>
			<!-- Required for e.g. schema registry's RestApp -->
			<classifier>tests</classifier>
			<scope>test</scope>
		</dependency>
```

## Kafka OPS
- https://kafka.apache.org/documentation/#operations
```
1. Alter configs for Kafka topics
# List topics
kafka-topics.sh --list --zookeeper localhost:2181

# Describe the topic
kafka-configs.sh --zookeeper localhost:2181 --entity-type topics --entity-name pluto_mvou_events

# The default retention time is 24 hours (86400000 millis)
kafka-configs.sh --zookeeper localhost:2181 --entity-type topics --entity-name TOPIC_NAME --alter --add-config retention.ms=5184000000


```
## Examples
- https://github.com/confluentinc/examples
- https://github.com/gwenshap/kafka-examples

## Cheatsheet
- http://ronnieroller.com/kafka/cheat-sheet