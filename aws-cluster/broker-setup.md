# Broker Setup

* **download binaries** `curl -O http://packages.confluent.io/archive/5.3/confluent-community-5.3.3-2.12.zip`
* **copy binaries**
* **Installation**

```text
mkdir confluent-kafka-5.3
mkdir confluent-kafka-5.3/data
mkdir confluent-kafka-5.3/software
sudo mv confluent-community-5.3.3-2.12.zip /confluent-kafka-5.3/software/
sudo unzip confluent-community-5.3.3-2.12.zip or tar xzf confluent-community-5.3.3-2.12.tar
```

* edit configuration files

```text
  broker.id=1
  listeners=PLAINTEXT://{ip}:9092
  advertised.listeners=PLAINTEXT://{ip}:9092
  num.io.threads=20
  num.network.threads=20
  log.dirs=/confluent-kafka-5.5/data/dir1
  num.partitions=6
  offsets.topic.replication.factor=3
  log.retention.hours=72
  zookeeper.connect=1{ip}:{ip}:2181{ip}:2181
  zookeeper.connection.timeout.ms=30000
```

