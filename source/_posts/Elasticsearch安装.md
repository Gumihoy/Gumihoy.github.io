---
title: Elasticsearch安装
date: 2019-01-15 14:15:53
categories: 
    - Elasticsearch
tags:
    - 全文搜索
    - Elasticsearch
---


---


## 下载

下载地址：https://www.elastic.co/downloads/elasticsearch

## 安装

```bash
# 解压
tar -zxvf elasticsearch-6.5.4.tar.gz
# copy

```

### 单机
```bash

```


### 集群

#### 配置

```bash
discovery.zen.ping.unicast.hosts: ["127.0.0.1:9300", "127.0.0.1:9301", "127.0.0.1:9302"]

```

> elasticsearch 不推荐使用多播，推荐使用单播



<br/>
## 问题

#### 异常详情
```
Exception in thread "main" java.nio.file.AccessDeniedException: /Library/elasticsearch-6.5.4/config/jvm.options
	at sun.nio.fs.UnixException.translateToIOException(UnixException.java:84)
	at sun.nio.fs.UnixException.rethrowAsIOException(UnixException.java:102)
	at sun.nio.fs.UnixException.rethrowAsIOException(UnixException.java:107)
	at sun.nio.fs.UnixFileSystemProvider.newByteChannel(UnixFileSystemProvider.java:214)
	at java.nio.file.Files.newByteChannel(Files.java:361)
	at java.nio.file.Files.newByteChannel(Files.java:407)
	at java.nio.file.spi.FileSystemProvider.newInputStream(FileSystemProvider.java:384)
	at java.nio.file.Files.newInputStream(Files.java:152)
	at org.elasticsearch.tools.launchers.JvmOptionsParser.main(JvmOptionsParser.java:60)
```
#### 解决方案
```bash
sudo chown -R 用户名 elasticsearch-6.5.4
```

<br/>

#### 异常详情
```
failed to send join request to master [{node-1}{woYxlU_VRVOCKYgA9QXl5g}{GQW9C2dXTV2KkaPaYP76Jw}{127.0.0.1}{127.0.0.1:9300}{ml.machine_memory=17179869184, ml.max_open_jobs=20, xpack.installed=true, ml.enabled=true}], reason [RemoteTransportException[[node-1][127.0.0.1:9300][internal:discovery/zen/join]]; nested: IllegalArgumentException[can't add node {node-2}{woYxlU_VRVOCKYgA9QXl5g}{aewcXbjZTq-brZG3gWiXPQ}{127.0.0.1}{127.0.0.1:9301}{ml.machine_memory=17179869184, ml.max_open_jobs=20, xpack.installed=true, ml.enabled=true}, found existing node {node-1}{woYxlU_VRVOCKYgA9QXl5g}{GQW9C2dXTV2KkaPaYP76Jw}{127.0.0.1}{127.0.0.1:9300}{ml.machine_memory=17179869184, xpack.installed=true, ml.max_open_jobs=20, ml.enabled=true} with the same id but is a different node instance]; ]
```
#### 解决方案
```bash
是因为复制的elasticsearch文件夹下包含了data文件中示例一的节点数据，需要把data文件下的文件清空。
```



<br/>

---
参考
