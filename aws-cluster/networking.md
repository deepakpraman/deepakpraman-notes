# Networking

* Add hosts entries \(mocking DNS\) - put relevant IPs here

```text
echo "ip1 kafka1 
      /ip2 zookeeper1 
      /ip3 kafka2 
      /ip4 zookeeper2 
      /ip5 kafka3 
      /ip6 zookeeper3" 
      /| sudo tee --append /etc/hosts
```



#### Ports

By default the Confluent Platform components use these ports to communicate. These ports must be open.

| Component | Port |
| :--- | :--- |
| Kafka brokers \(plain text\) | 9092 |
| Kafka inter-broker communication | 9091 |
| Confluent Control Center | 9021 |
| Kafka Connect REST API | 8083 |
| ksqlDB Server REST API | 8088 |
| Metadata Service \(MDS\) | 8090 |
| REST Proxy | 8082 |
| Schema Registry REST API | 8081 |
| ZooKeeper | 2181, 2888, 3888 |
| JMX-Exporter | 9075 |
| Prometheus | 9090 |
| Grafana | 3000 |
| Kafka-Lag-Exporter | 9080 |
| kafka-canary | 8085 |



