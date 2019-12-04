---
title: ZooKeeper安装
date: 2019-01-09 18:27:23
categories: 
    - ZooKeeper
tags:
    - ZooKeeper
---

ZooKeeper是一个分布式的，开放源码的分布式应用程序协调服务，是Google的Chubby一个开源的实现，是Hadoop和Hbase的重要组件。它是一个为分布式应用提供一致性服务的软件，提供的功能包括：配置维护、域名服务、分布式同步、组服务等。

　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　———摘自《百度百科》
<!-- more -->


## 下载

下载地址：https://mirrors.tuna.tsinghua.edu.cn/apache/zookeeper/

## 安装

```
$ cd /Library
$ tar -zxf zookeeper-3.4.13.tar.gz
$ cd zookeeper-3.4.13
$ mkdir data
```

### 配置
```
tickTime = 2000
dataDir = /Library/zookeeper-3.4.13/data
clientPort = 2181
initLimit = 5
syncLimit = 2
```

### 单机

### 集群



---




---
参考
官网：https://zookeeper.apache.org/
Github：
