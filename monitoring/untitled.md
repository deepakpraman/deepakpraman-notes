# Grafana

\*\*\*\*

## Kafka Monitoring Grafana

1. wget [https://s3-us-west-2.amazonaws.com/grafana-releases/release/grafana-5.2.1.linux-amd64.tar.gz](https://s3-us-west-2.amazonaws.com/grafana-releases/release/grafana-5.2.1.linux-amd64.tar.gz)
2. tar -zxvf grafana-.gz
3. rm grafana-.gz
4. mv grafana-\*/ grafana
5. cd grafana
6. enable anonymous authentication by setting

   vi conf/defaults.ini

   \`you can type "/anonymous" to jump the right line

   Insert following Content:

   \[auth.anonymous\]

   enabled = true

   org\_name = Main Org.

   org\_role = Admin

7. Start grafana:

   bin/grafana-server\`

   8.imports dashboards:

   [https://grafana.com/dashboards/721](https://grafana.com/dashboards/721)

   [https://grafana.com/dashboards/5468](https://grafana.com/dashboards/5468)

   [https://grafana.com/dashboards/762](https://grafana.com/dashboards/762)

8. [https://github.com/lightbend/kafka-lag-exporter/blob/master/grafana/Kafka\_Lag\_Exporter\_Dashboard.json](https://github.com/lightbend/kafka-lag-exporter/blob/master/grafana/Kafka_Lag_Exporter_Dashboard.json)

