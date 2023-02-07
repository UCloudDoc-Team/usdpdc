# 2 功能简介

## 2.1 USDP 核心功能

- 多集群管理能力，可配合底层网络策略实现多集群间的跨网络跨地域的访问及隔离；
- 集群主机管理能力，可线性扩展集群资源、主机状态监控、主机实例管理等；
- 集群大数据服务组件管理能力，对集群服务全方位的管理和维护、服务和实例的监控；
- 角色化配置管理，Key Value 级别配置同一角色组中的所有实例配置，并支持部分实例自定义扩展配置项；
- 可视化的服务配置管理、历史版本记录及回滚、实例配置过期待重启提醒等；
- 一键开启或关闭 Kerberos 安全模式；
- 中心化管理 UDH 源，按需自动下载并安装所需大数据服务组件；
- 集群级管理视图，包括服务便捷操作及集群资源监控等；
- 丰富的告警模板套用和灵活的自定义告警设置能力；
- 服务异常终止时自动拉起；
- 支持邮件、企业微信、钉钉、飞书等多种告警通知方式；
- 完善的主机环境修复及初始化工具；

## 2.2 UDH 发行版支持的大数据生态服务列表

UDH-3.0.0 中，已支持的大数据生态服务组件有：

| **服务**         | **版本** | **描述**                                                     |
| ---------------- | -------- | ------------------------------------------------------------ |
| HDFS             | 3.3.4    | Apache Hadoop 分布式文件系统 (HDFS) 是 Hadoop 应用程序使用的主要存储系统。HDFS 创建多个数据块副本并将它们分布在整个群集的计算主机上，以启用可靠且极其快速的计算功能。 |
| YARN             | 3.3.4    | Apache Hadoop MapReduce 2.0 (MRv2) 或 YARN 是支持 MapReduce 应用程序的数据计算框架（需要 HDFS）。 |
| Hive             | 3.1.3    | Apache Hive 数据仓库软件有助于使用 SQL 读取，写入和管理驻留在分布式存储中的大型数据集。 |
| TEZ              | 0.10.2   | Apache TEZ 是支持 DAG 作业的开源计算框架，它可以将多个有依赖的作业转换为一个作业从而大幅提升 DAG 作业的性能。 |
| HBase            | 2.4.11   | Apache HBase 是 Hadoop Database，是一个高可靠性、高性能、面向列、可伸缩的分布式存储系统。 |
| Phoenix          | 5.1.2    | Apache Phoenix 是 HBase 的 SQL 驱动，Phoenix 使得 HBase 支持通过 JDBC 的方式进行访问，并将你的 SQL 查询转成 HBase 的扫描和相应的动作。 |
| Impala           | 4.1.1    | Apache Impala 分布式计算服务。                               |
| Spark            | 3.2.3    | Apache Spark是一个通用的大数据分析引擎,具有高性能、易用和普遍性等特点。 |
| Hue              | 4.10.0   | Apache Hue 可视化管理服务。                                  |
| Sqoop            | 1.4.7    | Apache Sqoop 是一种用来将 Apache Hadoop 和结构化数据存储（如关系数据库）中的数据相互转移的工具。 |
| Flume            | 1.11.0   | Flume是Cloudera提供的一个高可用的，高可靠的，分布式的海量日志采集、聚合和传输的系统，Flume支持在日志系统中定制各类数据发送方，用于收集数据；同时，Flume提供对数据进行简单处理，并写到各种数据接受方（可定制）的能力。 |
| Kafka            | 2.8.1    | Apache Kafka 是一种高吞吐量的分布式发布订阅消息系统。        |
| Oozie            | 5.2.1    | Oozie 是群集中管理数据处理作业的工作流协调服务。             |
| DolphinScheduler | 3.1.0    | Apache DolphinScheduler 是一个分布式易扩展的可视化DAG工作流任务调度开源系统。 |
| Solr             | 8.11.2   | Apache Solr 基于Lucene的流行、高性能的开源企业级搜索平台。   |
| Prometheus       | 2.38.0   | Prometheus 是一个开源的系统监控和报警系统用于拉取大数据平台监控数据。 |
| Ranger           | 2.3.0    | Apache Ranger 授权服务。                                     |
| ZooKeeper        | 3.5.10   | Apache ZooKeeper 是用于维护和同步配置数据的集中服务。        |