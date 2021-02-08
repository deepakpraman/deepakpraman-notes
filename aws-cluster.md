# Cluster Setup

* Setup VMs
  * sudo yum update
  * sudo yum -y install wget ca-certificates zip net-tools vim nano tar netcat
* Setup java

  * sudo yum -y install openjdk-8-jdk

  `vi ~/.bash_profile export JAVA_HOME=/apps/jdk1.8.0_131/ export PATH=$PATH:/apps/jdk1.8.0_131/bin source ~/.bash_profile echo $JAVA_HOME echo $PATH`

* java -version
* set ulimit Add file limits configs - allow to open 100,000 file descriptors

`echo "* hard nofile 100000 soft nofile 100000" | sudo tee --append /etc/security/limits.conf`

* add storage
* Add hosts entries \(mocking DNS\) - put relevant IPs here

`echo "ip1 kafka1 ip2 zookeeper1 ip3 kafka2 ip4 zookeeper2 ip5 kafka3 ip6 zookeeper3" | sudo tee --append /etc/hosts`

* download binaries
  * curl -O [http://packages.confluent.io/archive/5.3/confluent-community-5.3.3-2.12.zip](http://packages.confluent.io/archive/5.3/confluent-community-5.3.3-2.12.zip)
* copy binaries

  `mkdir confluent-kafka-5.3`

  `mkdir confluent-kafka-5.3/data`

  `mkdir confluent-kafka-5.3/software`

  `sudo mv confluent-community-5.3.3-2.12.zip /confluent-kafka-5.3/software/`

  `sudo unzip confluent-community-5.3.3-2.12.zip or tar xzf confluent-community-5.3.3-2.12.tar`

* kafka 1
* kafka 2
* kafka 3
* kafka 4
* kafka 5
* zookeeper 1

  `cd /confluent-kafka-5.3/zookeeper/logs`

  `echo '1' >>myid`

* zookeeper 2

  `cd /confluent-kafka-5.3/zookeeper/logs`

  `echo '2' >>myid`

* zookeeper 3

  `cd /confluent-kafka-5.3/zookeeper/logs`

  `echo '3' >>myid`

* export KAFKA\_HEAP\_OPTS="-Xmx512m -Xms512M"
* edit configuration files
  * kafka 1
  * kafka 2
  * kafka 3
  * kafka 4
  * kafka 5
  * zookeeper 1
  * zookeeper 2
  * zookeeper 3
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

