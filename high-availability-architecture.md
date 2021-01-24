# High Availability Architecture

## Broker Outage Scenario

During a broker outage, all partition replicas on the broker become unavailable, so the affected partitions’ availability is determined by the existence and status of their other replicas. If a partition has no additional replicas, the partition becomes unavailable. If a partition has additional replicas that are in-sync, one of these in-sync replicas will become the interim partition leader. Finally, if the partition has addition replicas but none are in-sync, we have a choice to make: either we choose to wait for the partition leader to come back online–sacrificing availability — or allow an out-of-sync replica to become the interim partition leader–sacrificing consistency.

Once the broker comes back online, all its replicas will come back in sync with their partition-leaders. Once caught up, any replicas that were originally partition-leaders will become partition-leaders once again. It is worth noting that during the catch-up phase, the replicas are checking for missing messages based solely on message offsets. This detail will become important later on.

### Minimum In-Sync Replica

A high number of minimum in-sync replicas gives a higher persistence, but on the other hand, might reduce availability because the minimum number of replicas given must be available before a publish. If you have a 3 node cluster and the minimum in-sync replicas are set to 3, and one node goes down, the other two nodes will not able to receive any data. Only care about the minimum number of in-sync replicas when it comes to the availability of your cluster and reliability guarantees.

The leader is considered one of the in-sync replicas. It is included in the count of total min.insync.replicas.

