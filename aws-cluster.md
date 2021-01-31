# AWS - Cluster

* Setup VMs
  * sudo apt-get update
  * sudo apt-get -y install wget ca-certificates zip net-tools vim nano tar netcat
* Setup java
  * sudo apt-get -y install openjdk-8-jdk
* set ulimit
* add storage
* download binaries
  * curl -O [http://packages.confluent.io/archive/5.3/confluent-community-5.3.3-2.12.zip](http://packages.confluent.io/archive/5.3/confluent-community-5.3.3-2.12.zip)
* copy binaries

    `mkdir confluent-kafka-5.3`

    `mkdir confluent-kafka-5.3/data`

    `mkdir confluent-kafka-5.3/software`  

    `sudo mv confluent-community-5.3.3-2.12.zip /confluent-kafka-5.3/software/`

    `sudo unzip confluent-community-5.3.3-2.12.zip`

  * kafka 1
  * kafka 2
  * kafka 3
  * kafka 4
  * kafka 5

* zookeeper 1

  `/confluent-kafka-5.3/zookeeper/logs` 
  
  `echo '1' >>myid`
* zookeeper 2

  `/confluent-kafka-5.3/zookeeper/logs` 
  
  `echo '2' >>myid`

* zookeeper 3

  `/confluent-kafka-5.3/zookeeper/logs` 
  
  `echo '3' >>myid`



* prometheus



* grafana



* kafka lag exporter



* kafka lag tool



* kafDrop



* edit configuration files



* kafka 1
* kafka 2
* kafka 3
* kafka 4
* kafka 5
* zookeeper 1
* zookeeper 2
* zookeeper 3
* prometheus
* grafana
* kafka lag exporter
* kafka lag tool
* kafDrop
* Start zookeeper
* Start kafka
* Start kafka lag exporter
* Start prometheus
* Start grafana
* Start kafDrop
* Start Lag tool

