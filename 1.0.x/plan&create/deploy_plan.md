# 资源规划参考

本篇参考指南，旨在说明通过USDP私有化部署服务，协助用户来规划大数据服务的部署。用户可参考下文中的部署规模，来规划在您的基础资源及需求场景下，如何规划和利用基础资源，合理规划部署，使整体大数据服务更合理，更好的满足业务需要。



### 名词解释：

> 1. USDP Server：是用户独享的整个大数据系统的管理服务，提供一键安装包、修复工具、可视化的控制台。安装完成后，用户可通过USDP Server提供的控制台管理整个大数据系统，包括对多个大数据集群的管理。
>2. MySQL：是USDP Server依赖的管理元数据存储数据库。
> 3. Hadoop Cluster：是通过USDP控制台创建并管理的1-N个独立的大数据集群。
> 4. 大数据服务：是Hadoop集群中各个服务软件，例如：HDFS、Hive、Spark、HUE、Atlas等。
> 5. 服务组件：是各个大数据服务自带的服务构成的模块，例如：DataNode、NameNode是HDFS服务的两类重要的附件。



## 1.最小规模部署

本规划方案适用于：当业务量较小、资源较为紧俏时，以及您希望搭建一个最小规模的环境时。参考本章节内容，来协助实现智能大数据服务的部署参考。

因为USDP V1.0.0是基于Apache Hadoop 2.8.5，因此，HDFS数据存储副本为3，因此最小部署规模为3个节点。

| 节点/服务 | 最低配置                   | USDP Server | MySQL | NTP  | Hadoop Cluster | 大数据集群内各服务部署规划 |
| --------- | -------------------------- | ----------- | ----- | ---- | -------------- | -------------------------- |
| host01    | 8C 32G sys 60GB data 300GB | Y           | Y     | Y    | Cluster1-节点1 | 自行规划                   |
| host02    | 4C16G sys 60GB data 200GB  | -           | -     | -    | Cluster1-节点2 | 自行规划                   |
| host03    | 4C16G sys 60GB data 200GB  | -           | -     | -    | Cluster1-节点3 | 自行规划                   |

**注意：**您亦可将USDP Server、MySQL、NTP可以分散到上述host[01-03] 共三个节点上。

## 2.多节点规划

本规划方案适用于：当业务量较小、资源较为紧俏时，以及您希望搭建一个最小规模的环境，但USDP server、NTP服务器、MySQL服务器能与大数据集群相对独立的场景。参考本章节内容，来协助实现智能大数据服务的部署参考。

| 节点/服务 | 最低配置                   | USDP Server | MySQL | NTP  | Hadoop Cluster  | 大数据集群内各服务部署规划 |
| --------- | -------------------------- | ----------- | ----- | ---- | --------------- | -------------------------- |
| host01    | 8C 32G sys 60GB data 300GB | Y           | Y     | Y    | USDP Server节点 | 自行规划                   |
| host02    | 4C16G sys 60GB data 200GB  | -           | -     | -    | Cluster1-节点1  | 自行规划                   |
| host03    | 4C16G sys 60GB data 200GB  | -           | -     | -    | Cluster1-节点2  | 自行规划                   |
| host04    | 4C16G sys 60GB data 200GB  | -           | -     | -    | Cluster1-节点3  | 自行规划                   |

### 2.1若需要将MySQL与USDP Server分开部署，参考如下：

本规划方案适用于：当业务量较小、资源较为紧俏时，以及您希望搭建一个最小规模的环境，但USDP server、NTP服务器、MySQL服务器能与大数据集群相对独立，且MySQL服务器完全独立的场景。参考本章节内容，来协助实现智能大数据服务的部署参考。

| 节点/服务 | 最低配置                   | USDP Server | MySQL | NTP  | Hadoop Cluster  | 大数据集群内各服务部署规划 |
| --------- | -------------------------- | ----------- | ----- | ---- | --------------- | -------------------------- |
| host01    | 8C 32G sys 60GB data 300GB | Y           | -     | Y    | USDP Server节点 | 自行规划                   |
| host02    | 4C16G sys 60GB data 200GB  | -           | Y     | -    | MySQL节点       | 自行规划                   |
| host03    | 4C16G sys 60GB data 200GB  | -           | -     | -    | Cluster1-节点2  | 自行规划                   |
| host04    | 4C16G sys 60GB data 200GB  | -           | -     | -    | Cluster1-节点3  | 自行规划                   |
| host05    | 4C16G sys 60GB data 200GB  | -           | -     | -    | Cluster1-节点4  | 自行规划                   |

**注意：**您亦可将USDP Server、MySQL、NTP中的其中1到2个，分散部署到上述host[01-04] 共四个节点之外的节点去，例如MySQL可服用您现有其他业务系统的MySQL数据库。

## 3.多集群规划

本规划方案适用于：当业务较复杂、大数据分析业务在不同业务领域有独立隔离的诉求，资源相对较为充裕时，您希望通过USDP创建并管理多个大数据集群环境，并且USDP server、NTP服务器、MySQL服务器能与大数据集群相对独立的场景。参考本章节内容，来协助实现智能大数据服务的部署参考。

| 节点/服务 | 最低配置                   | USDP Server | MySQL | NTP  | Hadoop Cluster  | 大数据集群内各服务部署规划 |
| --------- | -------------------------- | ----------- | ----- | ---- | --------------- | -------------------------- |
| host01    | 8C 32G sys 60GB data 300GB | Y           | Y     | Y    | USDP Server节点 | 自行规划                   |
| host02    | 4C16G sys 60GB data 200GB  | -           | -     | -    | Cluster1-节点1  | 自行规划                   |
| host03    | 4C16G sys 60GB data 200GB  | -           | -     | -    | Cluster1-节点2  | 自行规划                   |
| host04    | 4C16G sys 60GB data 200GB  | -           | -     | -    | Cluster1-节点3  | 自行规划                   |
| Host05    | 4C16G sys 60GB data 200GB  | -           | -     | -    | Cluster2-节点1  | 自行规划                   |
| Host06    | 4C16G sys 60GB data 200GB  | -           | -     | -    | Cluster2-节点2  | 自行规划                   |
| Host07    | 4C16G sys 60GB data 200GB  | -           | -     | -    | Cluster2-节点3  | 自行规划                   |



当您已完成资源规划后，接下来就开始安装USDP吧，请前往 [USDP私有化部署流程](/usdpdc/1.0.x/plan&create/install)。