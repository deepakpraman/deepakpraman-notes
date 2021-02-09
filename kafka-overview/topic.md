# Topic

#### Create Topic

```text
./bin/kafka-topics --create --bootstrap-server localhost:9092 --replication-factor 3 --partitions 20 --topic myTopic
```

#### Topic List

Once you're strong enough, save the world:

```java
./bin/kafka-topics.sh --list --zookeeper localhost:2181
```

#### Describe a Topic

```text
./bin/kafka-topics --describe --zookeeper localhost:2181 --topic myTopic
```

#### Get Topic Offset

```text
./bin/kafka-run-class kafka.tools.GetOffsetShell --broker-list localhost:9092 --time -1 --topic myTopic
```

### TODO

Change the number of partitions and replication factor of a Topic

### Partitions

Topics contain logically related messages which are divided into a number of partitions. Partitions serve as our unit or ordering, replication, and parallelism

### Replication Factor

Topics are configured with a replication-factor, which determines the number of copies of each partition we have. All replicas of a partition exist on separate brokers \(the nodes of the Kafka cluster\). This means that we cannot have more replicas of a partition than we have nodes in the cluster.

### In-Sync Replicas

A replica is either the leader of its partition, or a follower of the leader. A follower can either be in-sync with the leader \(contains all the partition-leader’s messages, except for messages within a small buffer window\), or out-of-sync. The set of all in-sync replicas \(including the partition-leader\) is referred to as the ISR.

### min.insync.replicas
When a producer sets acks to "all" (or "-1"), this configuration specifies the minimum number of replicas that must acknowledge a write for the write to be considered successful. If this minimum cannot be met, then the producer will raise an exception (either NotEnoughReplicas or NotEnoughReplicasAfterAppend).
When used together, min.insync.replicas and acks allow you to enforce greater durability guarantees. A typical scenario would be to create a topic with a replication factor of 3, set min.insync.replicas to 2, and produce with acks of "all". This will ensure that the producer raises an exception if a majority of replicas do not receive a write.

Type:	int
Default:	1
Valid Values:	[1,...]
Server Default Property:	min.insync.replicas
Importance:	medium

### TODO

[https://kafka-tutorials.confluent.io/change-topic-partitions-replicas/ksql.html\#write-the-program-interactively-using-the-cli](https://kafka-tutorials.confluent.io/change-topic-partitions-replicas/ksql.html#write-the-program-interactively-using-the-cli) [https://kafka-tutorials.confluent.io/how-to-count-messages-on-a-kafka-topic/ksql.html](https://kafka-tutorials.confluent.io/how-to-count-messages-on-a-kafka-topic/ksql.html)

