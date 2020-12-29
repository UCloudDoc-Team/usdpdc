# USDP-V1.0.x 产品使用手册



## 一、产品概述

UCloud Smart Data Platform（简称 USDP），是 UCloud 推出的云上智能化、轻量级的大数据基础服务平台，能够帮您快速构建起大数据的分析处理能力。

USDP 构建于 UCloud 的云服务上，无缝集成云端 IaaS 资源能力，通过自研的 USDP Manager 管理工具，支持用户创建资源独享的大数据集群，在集群中部署 Hadoop、Hive、HBase、Spark、Flink、Presto 等开源的大数据组件，并对这些组件进行配置管理、监控告警、故障诊断等智能化的运维管理，从而帮助您快速构建起大数据的分析处理能力。



## 二、产品特点

本章节对 USDP 产品具备的特点进行介绍，帮助您了解它具备的主要能、用途、及优势等。

#### 1. 大数据开发“全家桶”

基于开放式的管理架构，USDP 集成了 30 余款开源的大数据组件，涵盖数据集成、数据存储、计算引擎、任务调度、权限管理等大数据处理的各个环节，全面性为业界之最。您可以根据自身业务特点和需求，从中选择相应的组件来搭建自己的大数据处理平台。

#### 2. 大数据运维“百宝箱”

源自多年的大数据运维经验积淀，USDP 为每款组件预置了完善的监控和告警模板，丰富的监控指标和灵活的告警方式，帮助您及时掌握各个组件的运行状况，进行必要的维护和优化。与此同时，智能化的故障诊断工具和专业的技术支持团队，为您的集群稳定运行保驾护航。

#### 3. 安全稳定

USDP 的底层资源为您所独享，集群位于独立的虚拟私有网络中，实现了有效的安全隔离。USDP 集成的各个组件编译自 Apache 社区稳定版本，经过了严格的兼容性测试和压力测试，关键性组件都支持高可用特性，确保集群稳定可靠运行。

#### 4. 弹性易用

针对大数据应用私有化部署场景，UCloud提供了友好且易于部署的 USDP 管理服务、大数据一体机服务。USDP 管理服务中向导式的操作流程和完善的场景案例，帮助您轻松上手使用。



## 三、功能简介

关于USDP平台的功能介绍，请点击前往 [功能介绍](usdpdc/1.0.x/release_notes) 查看。



## 四、规划及安装

通过本章节，我们将协助您完成初装前，对将要使用的服务器资源做出相应的合理规划，并提供安装部署、首个集群创建的参考文档，指导您快速部署。

* [资源规划](usdpdc/1.0.x/plan&create/deploy_plan)
* [部署流程](usdpdc/1.0.x/plan&create/install)
* [首次创建](usdpdc/1.0.x/plan&create/first_create)



## 五、控制台操作指南

大数据环境的管理员用户或开发者用户，可通过本章节了解到 USDP 各个模块的文档介绍，帮助您快速上手 USDP，了解如何在公有云环境中使用及管理 USDP 集群及服务的具体操作方法。

* 集群新增
* [节点管理](usdpdc/1.0.x/webconsole/node)
* [服务管理](usdpdc/1.0.x/webconsole/service)
* [监控管理](usdpdc/1.0.x/webconsole/monitor)
* [告警管理](usdpdc/1.0.x/webconsole/alarm)
* [USDP License管理](usdpdc/1.0.x/webconsole/license)



## 六、集群信息说明

如USDP安装后，服务的安装目录、数据存储目录等信息，服务的WebUIs登陆口令等信息，可参考如下内容。

* [各服务部署规则](usdpdc/1.0.x/cluster_notes/rule)
* [各服务WebUIs账号](usdpdc/1.0.x/cluster_notes/login)



## 七、开发指南

大数据业务的开发者用户在通过使用 USDP 智能大数据平台环境实现业务场景时，本章节内容为您介绍 USDP 所提供的各个开源大数据服务组件的部署及使用方式，帮助您快速开启数据分析业务开发之旅。

* [HDFS-开发指南](usdpdc/1.0.x/developer/hdfs)
* [Hive-开发指南](usdpdc/1.0.x/developer/hive)
* [HBase-开发指南](usdpdc/1.0.x/developer/hbase)
* [Ranger-开发指南](usdpdc/1.0.x/developer/ranger)
* [Atlas-开发指南](usdpdc/1.0.x/developer/atlas)



## 八、任务调度

大数据业务的开发者用户在通过使用 USDP 智能大数据平台环境，可借助 USDP 提供多种调度管理服务，协助用户完成高效管理任务的执行计划。

* [调度服务-UDS](usdpdc/1.0.x/schedule/uds)
* [调度服务-Airflow](usdpdc/1.0.x/schedule/airflow)



## 九、常见问题

您可能在使用中会遇到一些问题。

- [常见问题](usdpdc/1.0.x/FAQ)

