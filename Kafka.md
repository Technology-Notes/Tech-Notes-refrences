https://kafka.apache.org/documentation/

https://community.hortonworks.com/articles/80813/kafka-best-practices-1.html

https://sookocheff.com/post/kafka/kafka-in-a-nutshell/
```
Consumers and Consumer Groups

Consumers read from any single partition, allowing you to scale throughput of message consumption in a similar fashion to message production. Consumers can also be organized into consumer groups for a given topic — each consumer within the group reads from a unique partition and the group as a whole consumes all messages from the entire topic. If you have more consumers than partitions then some consumers will be idle because they have no partitions to read from. If you have more partitions than consumers then consumers will receive messages from multiple partitions. If you have equal numbers of consumers and partitions, each consumer reads messages in order from exactly one partition.
```

## Kafka, Spark, Avro Integration
- http://www.hongyusu.com/amt/spark-streaming-kafka-avro-and-registry.html
- https://github.com/opencore/kafka-spark-avro-example

## Kafka Schema Registry
- https://github.com/confluentinc/schema-registry
- https://github.com/Landoop/schema-registry-ui
- https://dzone.com/articles/kafka-avro-serialization-and-the-schema-registry
- http://cloudurable.com/blog/kafka-avro-schema-registry/index.html
```
The compatibility checks value is one of the following:

NONE - don’t check for schema compatibility
FORWARD - check to make sure last schema version is forward compatible with new schemas
BACKWARDS (default) - make sure new schema is backwards compatible with latest
FULL - make sure new schema is forwards and backwards compatible from latest to new and from new to latest
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