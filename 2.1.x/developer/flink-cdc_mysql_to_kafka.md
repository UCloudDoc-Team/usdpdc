# Flink-CDC同步Mysql数据到Kafka

## 1. 环境准备

- USDP  v2.1.2

- Mysql  v15.1

- Kafka  v2.11-2.4.0

- Flink  v1.13.2 on Yarn

## 2. 下载依赖包

- [flink-sql-connector-kafka_2.11-1.13.2.jar](https://repo.maven.apache.org/maven2/org/apache/flink/flink-sql-connector-kafka_2.11/1.13.2/flink-sql-connector-kafka_2.11-1.13.2.jar)  若Flink为其他版本，点击[这里](https://repo.maven.apache.org/maven2/org/apache/flink/flink-sql-connector-kafka_2.11/)查找jar包；

- [flink-sql-connector-mysql-cdc-1.3.0.jar](https://repo.maven.apache.org/maven2/com/alibaba/ververica/flink-sql-connector-mysql-cdc/1.3.0/flink-sql-connector-mysql-cdc-1.3.0.jar)  若需要其他版本，点击[这里](https://repo.maven.apache.org/maven2/com/alibaba/ververica/flink-sql-connector-mysql-cdc/)查找jar包；

如果你是更高版本的Flink，可以自行https://github.com/ververica/flink-cdc-connectors下载新版mvn clean install -DskipTests 自己编译。   包下载好之后，放在Flink lib目录（/srv/udp/2.0.0.0/flink/lib）下：

![](../images/developer/Flink/flink-lib.png)

## 3. 启动Flink SQL Client

### 3.1 通过Flink启动Yarn的一个资源队列application 

进入flink bin目录（/srv/udp/2.0.0.0/flink/bin），执行：

```shell
./yarn-session.sh -d -s 1 -jm 1024 -tm 2048 -qu root.sparkstreaming -nm flink-cdc-kafka
```

![](../images/developer/Flink/yarn-applications.png)

### 3.2 进入Flink SQL 命令行

注意，需指定关联已创建的资源队列“flink-cdc-kafka”

```shell
./sql-client.sh embedded -s flink-cdc-kafka
```

![](../images/developer/Flink/flink-sql-client.png)

## 4. 测试数据准备

Mysql 数据准备

```shell
mysql> create database 'flink_test';
mysql> use flink_test;
```

测试表及样本数据

```sql
CREATE TABLE `user_view` (
`id` int(11) NOT NULL AUTO_INCREMENT,
`user_id` int(11) NOT NULL,
`user_name` varchar(10) NOT NULL,
`age` int(3) NOT NULL,
`time` datetime NOT NULL,
PRIMARY KEY (`id`),
KEY `time` (`time`),
KEY `users` (`user_id`,`user_name`) USING BTREE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--样本数据--
INSERT INTO `user_view` VALUES ('1', '1', '托尼·斯塔克', '32', '2020-04-24 13:14:00');
INSERT INTO `user_view` VALUES ('2', '1', '斯蒂夫·罗杰斯', '41', '2020-04-24 13:14:00');
INSERT INTO `user_view` VALUES ('3', '1', '布鲁斯·班纳', '33', '2020-04-24 13:14:00');
INSERT INTO `user_view` VALUES ('4', '1', '托尔', '50', '2020-04-24 13:14:00');
INSERT INTO `user_view` VALUES ('5', '8', '娜塔莎·罗曼诺夫', '29', '2020-05-14 13:14:00');
INSERT INTO `user_view` VALUES ('6', '8', '克林特·巴顿', '36', '2020-05-13 13:14:00');
INSERT INTO `user_view` VALUES ('7', '8', '玛丽亚·希尔', '31', '2020-04-24 13:14:00');
INSERT INTO `user_view` VALUES ('8', '8', '尼克·弗瑞', '43', '2020-04-23 13:14:00');
INSERT INTO `user_view` VALUES ('9', '8', '菲尔·科尔森', '42', '2020-05-13 13:14:00');
```

检查数据

![](../images/developer/Flink/mysql-table-select.png)

## 5. 同步数据

### 5.1 创建关联Mysql表的Flink数据表

```sql
Flink SQL>
> show databases;
+------------------+
|    database name |
+------------------+
| default_database |
+------------------+
1 row in set


Flink SQL> use default_database;
[INFO] Execute statement succeed.
Flink SQL> show tables;
+------------------+
|       table name |
+------------------+
| user_view_source |
+------------------+
1 row in set

Flink SQL>
```

创建Flink表

```sql
CREATE TABLE user_view_source (
`id` int,
`user_id` int,
`user_name` varchar,
`age` int,
`time` timestamp,
PRIMARY KEY (`id`) NOT ENFORCED
) WITH (
'connector' = 'mysql-cdc',
'hostname' = 'usdp212-1',
'port' = '3306',
'username' = 'root',
'password' = 'S2sd9d8sjduss',
'database-name' = 'flink_test',
'table-name' = 'user_view'
);
```

查询源表数据

```sql
Flink SQL> select * from user_view_source;
```

若查询正常，则如下显示

![](../images/developer/Flink/flink-sql-select.png)

此时，在Flink SQL Client中操作这张表，就相当于在操作Mysql里面对应的那张“user_view”表。

若执行中碰到如下报错，请更该mysql的binlog格式为row，并重启mysql；

```shell
……
[ERROR] Could not execute SQL statement. Reason:
org.apache.kafka.connect.errors.ConnectException: The MySQL server is not configured to use a ROW binlog_format, which is required f this connector to work properly. Change the MySQL configuration to use a binlog_format=ROW and restart the connector.
```

### 5.2 创建关联kafka topic的Flink数据表

```sql
CREATE TABLE user_view_kafka_sink(
`id` int,
`user_id` int,
`user_name` varchar,
`age` int,
`time` timestamp,
PRIMARY KEY (`id`) NOT ENFORCED
) WITH (
'connector' = 'upsert-kafka',
'topic' = 'flink-cdc-kafka',
'properties.bootstrap.servers' = 'usdp212-1:9092',
'properties.group.id' = 'flink-cdc-kafka-group',
'key.format' = 'json',
'value.format' = 'json'
);
```

通过Flink建表，kafka里面的flink-cdc-kafka这个topic会被**自动创建**；如果想要给topic指定一些属性，可以在此之前手动创建好topic；当操作Flink表user_view_kafka_sink，并往里面插入数据，可已看到kafka中已经有数据了。

### 5.3 同步数据

建立同步任务，可以执行如下Flink SQL：

```sql
Flink SQL> insert into user_view_kafka_sink select * from user_view_source;
```

此时，可退出flink sql-client，并进入flink web-ui，即可看到mysql表数据已经同步到kafka topic中了。

![](../images/developer/Flink/flink-webui-yarn-tracking-url.png)

并且，对mysql表再次进行数据插入，kafka仍会保持同步更新。

![](../images/developer/Flink/kafka-console-consumer.png)
