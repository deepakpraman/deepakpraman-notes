# JMX Exporter

1. Download jmx\_prometheus\_javaagent agent & config
2. mkdir prometheus
3. cd prometheus
4. wget [https://repo1.maven.org/maven2/io/prometheus/jmx/jmx\_prometheus\_javaagent/0.3.1/jmx\_prometheus\_javaagent-0.3.1.jar](https://repo1.maven.org/maven2/io/prometheus/jmx/jmx_prometheus_javaagent/0.3.1/jmx_prometheus_javaagent-0.3.1.jar)
5. wget [https://raw.githubusercontent.com/prometheus/jmx\_exporter/master/example\_configs/kafka-0-8-2.yml](https://raw.githubusercontent.com/prometheus/jmx_exporter/master/example_configs/kafka-0-8-2.yml)
6. export KAFKA\_OPTS="-javaagent:/apps/kafka/prometheus/jmx\_prometheus\_javaagent-0.3.1.jar=7072:/apps/kafka/prometheus/kafka-2\_0\_0.yml"
7. nohup apps/kafka/confluent-5.5.3/bin/kafka-server-start /apps/kafka/confluent-5.5.3/etc/kafka/server.properties &

