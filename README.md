# Hbase+SpringBoot

#### 介绍
Hbase+Spring boot实战分布式文件存储

Hos服务项目

关键问题有 Hadoop与Spark的部署问题

### Hadoop 部署


config / hdfs-site.xml

```
<?xml version="1.0"?>
<configuration>
    <property>
        <name>dfs.namenode.name.dir</name>
        <value>file:///root/hdfs/namenode</value>
        <description>NameNode directory for namespace and transaction logs storage.</description>
    </property>
    <property>
        <name>dfs.datanode.data.dir</name>
        <value>file:///root/hdfs/datanode</value>
        <description>DataNode directory</description>
    </property>
    <property>
        <name>dfs.replication</name>
        <value>2</value>
    </property>
</configuration>

```