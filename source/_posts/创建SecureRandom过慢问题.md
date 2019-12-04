---
title: 创建SecureRandom过慢问题
date: 2018-12-13 20:14:30
categories: 
    - Tomcat
tags:
    - Java
    - Tomcat
    - Slow
---

Linux 环境Tomcat启动项目 创建SecureRandom过慢，报如下警告信息
```
 o.a.c.util.SessionIdGeneratorBase        : Creation of SecureRandom instance for session ID generation using [SHA1PRNG] took [28,420] milliseconds.
```

这个问题很多人遇到过，tomcat的wiki里面还单独列出来作为加速启动的一个方面：
https://wiki.apache.org/tomcat/HowTo/FasterStartUp#Entropy_Source


tomcat7/tomcat8的session id的生成主要通过`java.security.SecureRandom`生成随机数来实现，随机数算法使用的是`SHA1PRNG`

在sun/oracle的jdk里，这个算法的提供者在底层依赖到操作系统提供的随机数据，在linux上，与之相关的是`/dev/random`和`/dev/urandom` 
** /dev/random **
```
在读取时，/dev/random设备会返回小于熵池噪声总数的随机字节。
/dev/random可生成高随机性的公钥或一次性密码本。
若熵池空了，对/dev/random的读操作将会被阻塞，直到收集到了足够的环境噪声为止
```

** /dev/urandom 则是一个非阻塞的发生器 **
```
dev/random的一个副本是/dev/urandom （”unlocked”，非阻塞的随机数发生器），它会重复使用熵池中的数据以产生伪随机数据。
这表示对/dev/urandom的读取操作不会产生阻塞，但其输出的熵可能小于/dev/random的。
它可以作为生成较低强度密码的伪随机数生成器，不建议用于生成高强度长期密码。
```

<!-- more -->

** 解决方法：**

采用非阻塞的熵源(entropy source)

```
系统属性:
-Djava.security.egd=file:/dev/./urandom

文件修改：$JAVA_HOME/jre/lib/security/java.security
securerandom.source=file:/dev/urandom
```