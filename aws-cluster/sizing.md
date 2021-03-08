# Sizing

Based on the anticipated data rate, you can calculate how much disk space may be required and how to trade off the following variables to meet your needs and keep Kafka healthy.

* Disk Size - Multi-TB hard drives have more capacity compared to SSDs, but trade off read and write performance.
* Number of Partitions - Using more partitions increases throughput per topic through parallelism. It also allows more drives to be used, one per partition, which increases capacity. Note that Kafka only preserves message order per partition, not over a whole, multi-partition topic. Topic messages can be partitioned randomly or by hashing on a key.
* Replication Factor - The replication factor provides resiliency for a partition. Replicas are spread across available brokers, therefore your replication factor is always &lt;= the number of brokers in your cluster. It must be accounted for when determining disk requirements because there is no difference between how much space a leader partition and a replica partition uses. The total number of partitions for a given a topic is the number of partitions \* the replication factor.
* Dedicated Drives - Using dedicated drives for the Kafka brokers not only improves performance, by removing other activity from the drive, but should the drive become full, then other services that need drive space will not be adversely affected.
* Do not use RAID for fault tolerance. Kafka provides fault tolerance guarantees at the application layer \(with topic replication factor\) making fault tolerance at the hard disk level redundant.

To estimate disk requirements for your need, per broker, begin by estimating the projected usage. Here is an example.

| Quantity | Example | Discussion |
| :--- | :--- | :--- |
| Average topic message throughput \(MT\) | 500 msg/sec | For each topic, how many messages on average per second. |
| Average message size \(MS\) | 5 KB | Note that Kafka works best with messages under 1MB in size. |
| Broker message retention length \(RL\) | 24 hours \(86400 seconds\) | The Kafka cluster retains all published messages whether or not they have been consumed for a configurable period of time.  For example if the log retention is set to 24 hours, then for 24 hours after a message is published it is available for consumption, after which it will be discarded to free up space. |
| Number of topics \(NT\) | 1 |  |
| Average replication factor \(NR\) | 2 |  |
| Number of Kafka Brokers \(KB\) | 3 |  |



Disk size per broker = \( MT x MS x RL x NT x NR \) / KB

= \(500 x 5 x 86400 x 1 x 2\) / 3 = 144000000 KB = 138 GB



#### Kafka Broker Memory \(RAM\) Sizing

Memory \(RAM\) per broker = \(MT x MS x 3600\)

= 9000000 KB = 9 GB

