# Kafka-Lag-Exporter

1. mkdir kafka-Lag-Exporter
2. wget [https://github.com/lightbend/kafka-lag-exporter/releases](https://github.com/lightbend/kafka-lag-exporter/releases)
3. application.conf

```text
kafka-lag-exporter {
  reporters.prometheus.port = 8355
  clusters = [
    {
      name = "non-prod-cluster"
      bootstrap-brokers = "localhost:9072,localhost:9073,localhost:9074,localhost:9075,localhost:9076"
      labels = {
        location = "ae"
        zone = "middle-east"
      }
    }
  ]
}
```

4. mkdir conf

5. cd conf

6.wget [https://github.com/lightbend/kafka-lag-exporter/blob/master/examples/standalone/logback.xml](https://github.com/lightbend/kafka-lag-exporter/blob/master/examples/standalone/logback.xml)

7 ./bin/kafka-lag-exporter  -Dconfig.file=/apps/kafka/confluent-5.5.3/tools/kafka-lag-exporter-0.6.5/config/application.conf  -Dlogback.configurationFile=/apps/kafka/confluent-5.5.3/tools/kafka-lag-exporter-0.6.5/config/logback.xml

