# Zookeeper Setup

* zookeeper 1

  `cd /confluent-kafka-5.3/zookeeper/logs`

  `echo '1' >>myid`

* zookeeper 2

  `cd /confluent-kafka-5.3/zookeeper/logs`

  `echo '2' >>myid`

* zookeeper 3

  `cd /confluent-kafka-5.3/zookeeper/logs`

  `echo '3' >>myid`

zookeeper.properties

```text
tickTime=2000
dataDir=/var/lib/zookeeper/
clientPort=2181
initLimit=5
syncLimit=2
server.1=zoo1:2888:3888
server.2=zoo2:2888:3888
server.3=zoo3:2888:3888
autopurge.snapRetainCount=3
autopurge.purgeInterval=24
```

