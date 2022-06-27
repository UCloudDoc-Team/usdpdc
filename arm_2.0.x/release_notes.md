# 信创版功能简介



### <center>[功能点概述](usdpdc/arm_2.0.x/release_notes?id=一、信创版功能点概述)   |  [适配兼容详情](usdpdc/arm_2.0.x/release_notes?id=二、适配兼容详情)  |  [支持的大数据生态服务](usdpdc/arm_2.0.x/release_notes?id=三、信创版支持的大数据生态服务)</center>



### 一、信创版功能点概述

- 支持完善的服务器初装时初始化修复工具；

- 支持友好的Web浏览器管理控制台；

- 支持多集群管理；配合设备网络策略可实现多集群间的访问隔离；

- 支持存储集群与计算集群分离架构；

- 支持集群节点管理，如节点监控、资源私用率、节点状态等；

- 支持集群大数据服务的服务监控、组件管理、组件启停、组件扩展及删除，组件滚动重启；

- 支持丰富的监控模板和视图；

- 支持大数据服务的扩展；

- 支持服务配置文件修改；

- 支持配置文件修改后集群服务自动检测需要重启生效的依赖服务提示；

- 支持各大数据服务Web UIs便捷访问；

- 支持服务异常终止时自动拉起；

- 提供丰富的监控模板，涵盖服务器监控及大数据服务监控等；

- 支持监控模板规则自定义；

- 支持通知组、通知对象管理；

- 支持邮件、微信、钉钉、回调函数等多种告警通知方式；

- 支持控制台与系统配置双向同步；

- 提供丰富的智库和异常修复诊断及建议；

- 支持授权证书管理和查看功能；

- 支持服务日志查看及下载；

  

### 二、适配兼容详情

| 认证               | 兼容                                                         | 状态   |
| ------------------ | ------------------------------------------------------------ | ------ |
| 华为鲲鹏技术认证   | Kunpeng920 CPU                                               | 已适配 |
| 飞腾技术认证       | S2500 CPU                                                    | 已适配 |
| 麒麟NeoCertify认证 | 银河麒麟操作系统（飞腾版）V10</br>银河麒麟操作系统（鲲鹏版）V10 | 已适配 |



### 三、信创版支持的大数据生态服务

USDP-2.0.x 中，已支持的大数据生态服务有：

| 大数据生态服务 | 服务版本 | 描述                      |
| -------------- | -------- | ------------------------- |
| **计算服务**   |          |                           |
| FLINK          | 1.13.1   | 分布式计算引擎            |
| HIVE           | 3.0.0    | 最常用的 HQL 数仓工具     |
| PHOENIX        | 5.1.1    | HBase SQL 化查询分析工具  |
| SPARK          | 3.1.2    | 分布式计算引擎            |
| TEZ            | 0.10.0   | 优化 MapReduce 任务的 DAG |
| YARN           | 3.1.1    | 分布式资源调度服务        |
| **存储服务**   |          |                           |
| HDFS           | 3.1.1    | 分布式存储服务            |
| HBASE          | 2.1.10   | 分布式非关系型数据库      |
| ZOOKEEPER      | 3.4.13   | 分布式注册中心服务        |
| **监控服务**   |          |                           |
| ALERTMANAGER   | 0.21.0   | 发送监控告警信息          |
| GRAFANA        | 6.5.1    | 展示监控数据              |
| INFLUXDB       | 1.8.0    | 存储监控数据              |
| NODEEXPORTER   | 1.0.0    | 读取节点资源监控指标      |
| PROMETHEUS     | 2.18.1   | 拉取监控数据              |



了解USDP [更多USDP发布的版本](/usdpdc/version_list)



### 合作咨询

USDP专业版 [合作咨询](https://spt.ucloud.cn/30001)