# Cluster Setup

## Setting up the Platform

### Setup VMs

* sudo yum update
* sudo yum -y install wget ca-certificates zip net-tools vim nano tar netcat

### Setup java

* sudo yum -y install openjdk-8-jdk

  `vi ~/.bash_profile`

  `export JAVA_HOME=/apps/jdk1.8.0_131/ export PATH=$PATH:/apps/jdk1.8.0_131/bin`

  `source ~/.bash_profile`

  `echo $JAVA_HOME`

  `echo $PATH`

* java -version
* set ulimit Add file limits configs - allow to open 100,000 file descriptors

`echo "* hard nofile 100000 soft nofile 100000" | sudo tee --append /etc/security/limits.conf`

* add storage
* Add hosts entries \(mocking DNS\) - put relevant IPs here

`echo "ip1 kafka1 ip2 zookeeper1 ip3 kafka2 ip4 zookeeper2 ip5 kafka3 ip6 zookeeper3" | sudo tee --append /etc/hosts`

## Setting up Kafka

* export KAFKA\_HEAP\_OPTS="-Xmx512m -Xms512M"

**Get Confluent Kafka \(Community Edition\) Software**

* download binaries
  * curl -O [http://packages.confluent.io/archive/5.3/confluent-community-5.3.3-2.12.zip](http://packages.confluent.io/archive/5.3/confluent-community-5.3.3-2.12.zip)
* copy binaries

  `mkdir confluent-kafka-5.3`

  `mkdir confluent-kafka-5.3/data`

  `mkdir confluent-kafka-5.3/software`

  `sudo mv confluent-community-5.3.3-2.12.zip /confluent-kafka-5.3/software/`

  `sudo unzip confluent-community-5.3.3-2.12.zip or tar xzf confluent-community-5.3.3-2.12.tar`

## Setting up Zookeeper

* zookeeper 1

  `cd /confluent-kafka-5.3/zookeeper/logs`

  `echo '1' >>myid`

* zookeeper 2

  `cd /confluent-kafka-5.3/zookeeper/logs`

  `echo '2' >>myid`

* zookeeper 3

  `cd /confluent-kafka-5.3/zookeeper/logs`

  `echo '3' >>myid`

## Setting up Brokers

* edit configuration files

`broker.id=1 host.name={ip} advertised.host.name={ip} listeners=PLAINTEXT://{ip}:9092 advertised.listeners=PLAINTEXT://{ip}:9092 num.io.threads=20 num.network.threads=20 log.dirs=/confluent-kafka-5.3/data/ num.partitions=6 offsets.topic.replication.factor=3 transaction.state.log.replication.factor=3 transaction.state.log.min.isr=3 log.retention.hours=72 zookeeper.connect=zookeeper1:2181,zookeeper2:2181,zookeeper3:2181 zookeeper.connection.timeout.ms=30000`

Repeat for all nodes 1..5

## Starting the Applications

* Start zookeeper
  * zookeeper 1
  * zookeeper 2
  * zookeeper 3
* Start kafka
  * kafka 1
  * kafka 2
  * kafka 3
  * kafka 4
  * kafka 5

