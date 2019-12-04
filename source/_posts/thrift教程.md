---
title: thrift教程
date: 2018-11-23 17:32:06
categories:
    - Thrift
tags:
    - RPC
    - Thrift
---

 Apache Thrift 采用接口描述语言定义并创建服务，支持可扩展的跨语言服务开发，所包含的代码生成引擎可以在多种语言中，如 C++, Java, Python, PHP, Ruby, Erlang, Perl, Haskell, C#, Cocoa, Smalltalk 等创建高效的、无缝的服务，其传输数据采用二进制格式，相对 XML 和 JSON 体积更小，对于高并发、大数据量和多语言的环境更有优势


　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　———摘自《thrift.apache.org》
<!-- more -->

---

<br/>
### 介绍
Thrift通过IDL（Interface Definition Language，接口定义语言）来定义RPC（Remote Procedure Call，远程过程调用）的接口和数据类型，然后通过thrift编译器生成不同语言的代码，并由生成的代码负责RPC协议层和传输层的实现。


![thrift-layers](thrift-layers.png)

<br/>
### 安装
现下载：https://thrift.apache.org/download
官网安装：https://thrift.apache.org/docs/install/

<br/>
#### 快速安装

```bash
# 安装命令
brew install thrift
# 卸载命令
brew uninstall thrift
```

<br/>
#### 源安装

** 1、Install Boost **
Boost 下载地址：https://www.boost.org/
```bash
./bootstrap.sh
sudo ./b2 threading=multi address-model=64 variant=release stage install
```

** 2、Install libevent **
libevent 下载地址：http://libevent.org/
```bash
./configure --prefix=/usr/local
make
sudo make install
```

** 3、Building Apache Thrift **
```bash
./configure --prefix=/usr/local/ --with-boost=/usr/local --with-libevent=/usr/local
```


<br/>
### 使用

1、pom文件导入thrift依赖
```xml
<!-- https://mvnrepository.com/artifact/org.apache.thrift/libthrift -->
<dependency>
    <groupId>org.apache.thrift</groupId>
    <artifactId>libthrift</artifactId>
    <version>0.11.0</version>
    <type>pom</type>
</dependency>
```


```java

```





<br/>
### 源码分析






<br/>

---
参考
[thrift官网](https://thrift.apache.org/)
[thrift-Github](https://github.com/apache/thrift)
https://www.kancloud.cn/digest/thrift/