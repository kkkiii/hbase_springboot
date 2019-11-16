# Hbase+SpringBoot

#### 介绍
Hbase+Spring boot实战分布式文件存储

Hos服务项目

关键问题有 Hadoop与Spark的部署问题

### Hadoop伪分布式集群安装

- ~/hadoop-2.7.7/sbin

该目录是终端脚本运行文件的

- ~/hadoop-2.7.7/etc/hadoop

该目录下进行各种配置

1. 配置 hadoop-env.sh 文件

配置 JAVA_HOME 变量

JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk-10.jdk/Contents/Home

2. hdfs-site.xml



```
<configuration>
    <property>
        <name>dfs.namenode.name.dir</name>
        <value>file:/Users/liufan/hadoop_data/dfs/name</value>
        <description>NameNode directory for namespace and transaction logs storage.</description>
    </property>
    <property>
        <name>dfs.datanode.data.dir</name>
        <value>file:/Users/liufan/hadoop_data/dfs/data</value>
        <description>DataNode directory</description>
    </property>
    <property>
        <name>dfs.replication</name>
        <value>1</value>
    </property>
</configuration>

```

3. core-site.xml

```
<configuration>
    <property>
        <name>fs.defaultFS</name>
        <value>hdfs://hadoop-master:9000/</value>
    </property>
    <property>
        <name>hadoop.tmp.dir</name>
        <value>file:/Users/liufan/hadoop_data/</value>
    </property>
</configuration>
```

4. 更多配置，查询官方文档

https://hadoop.apache.org/docs/r2.4.1/hadoop-project-dist/hadoop-hdfs/hdfs-default.xml

https://hadoop.apache.org/docs/r2.8.0/hadoop-project-dist/hadoop-common/core-default.xml

