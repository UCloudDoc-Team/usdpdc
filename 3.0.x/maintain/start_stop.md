# 大数据组件起停顺序

!> 注意有多页的情况下，调整每页展示的实例数量后进行选择，然后进行批量起停

## 服务启动顺序（如果有）

```
NodeExporter
InfluxDB
Prometheus
Grafana
AlertManager
Ranger
ZooKeeper
HDFS
YARN
Tez
Hive
HBase
Phoenix
Solr
Spark
Impala
Hue
Kafka
KafkaEagle
Sqoop
Flume
Kylin
Flink
Livy
Zeppelin
ZKUI
Oozie
Atlas
```

## 服务关闭顺序 倒着来
