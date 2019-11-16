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

还要在```/etc/hosts/``` 中配置 hadoop-master 的地址的，否则会失败的

```
127.0.0.1 hadoop-master
```

4. 更多配置，查询官方文档

https://hadoop.apache.org/docs/r2.4.1/hadoop-project-dist/hadoop-hdfs/hdfs-default.xml

https://hadoop.apache.org/docs/r2.8.0/hadoop-project-dist/hadoop-common/core-default.xml

5. ~/hadoop-2.7.7/bin

进入目录下，执行命令：

```
./hdfs namenode -format
```

最后几行日志是这个，说明文件生成成功：

```
19/11/16 11:13:55 INFO namenode.NNStorageRetentionManager: Going to retain 1 images with txid >= 0
19/11/16 11:13:55 INFO util.ExitUtil: Exiting with status 0
19/11/16 11:13:55 INFO namenode.NameNode: SHUTDOWN_MSG:
/************************************************************
SHUTDOWN_MSG: Shutting down NameNode at FeanLau-Pro.local/10.188.215.153
************************************************************/
```

创建文件成功，但是启动集群失败！！

6. ~/hadoop-2.7.7/sbin

启动集群

```
./start-dfs.sh
```

出现了问题，解决mac下 ssh: connect to host localhost port 22: Connection refused

```
ssh localhost
//ssh: connect to host localhost port 22: Connection refused
sudo systemsetup -f -setremotelogin on

ssh localhost 
//ok
```

配置了之后，依然启动失败



