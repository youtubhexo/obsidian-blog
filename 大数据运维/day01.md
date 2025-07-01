提问: 面试题：

hadoop中组件有哪些？

hadoop组件中有哪些节点，节点的作用又是什么？

nn  dn

rm

nm


### 数据分类
结构化数据
     业务数据库中历史数据
非结构化数据
       Ngginx 业务日志等
半结构化数据
      JSON xml

### HDFS高可用集群架构

journalnode 负责namenode  元数据的同步,类似蓝奏云

namenode 在hadoop2的架构中,最多有两个

datanode,可以有多个
zookpeeper 负责实现让连个namenode 主备之间的切换
zkfc进程, 让namenode连接zk

### yarn 高可用集群架构

ResourceManager RS  主节点
NodeNanager  从节点

































