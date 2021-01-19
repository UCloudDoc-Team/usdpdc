# 为USDP新增服务器节点

在使用USDP服务过程中，可能随着用户业务需求增长，或业务调整，现有的大数据集群资源已不足以满足需求时，可能需要为USDP服务扩展可管理的服务器节点，在准备好服务器并安装操作系统，仍需要通过USDP提供的一键修复工具，对新增节点进行修复，USDP支持批量节点扩展。

参考如下内容，进行扩展节点的修复操作：

## 1. 服务器节点修复

### 1.1 检查your.properties 配置的信息

检查 your.properties 文件的参数项 host.single.info.Path，即新增节点信息存放的绝对路径。对于该配置文件其他参数项无需改动。

     host.single.info.Path=/opt/usdp-srv/usdp/repair/host_single_info.txt

### 1.2 配置host_single_info.txt文件

与4.1节中的全量修复类似， 文件中每行为一个节点信息，从左至右依次为：内网IP，节点密码，SSH端口号，即将自动修改生效的主机名。具体示例如下：

~~~shell
      127.0.0.1 your-node-root-password 22 udp01
      127.0.0.1 your-node-root-password 22 udp02
      127.0.0.1 your-node-root-password 22 udp03
~~~

修改完上述配置文件，即可进入 repair 目录执行如下修复命令


      bash repair.sh  initSingle  /opt/usdp-srv/usdp/repair/your.properties

!> 注意：</br> 1. 在host_single_info.txt文件中，仅需配置每次新增的节点信息即可，若存在已修复过的节点信息时，在下次运行“repair.sh  initSingle”指令前，请清除。</br> 2. jdk 安装在 /opt/module 下面，不允许随意删除，否则 java 环境失效。



## 2. 新增大数据集群

此处，看参考 [新增大数据集群](https://docs.ucloud.cn/usdpdc/1.0.x/webconsole/clusters?id=一、新增大数据集群)



## 3. 为已有集群添加节点

