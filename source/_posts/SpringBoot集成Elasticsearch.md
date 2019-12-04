---
title: SpringBoot集成Elasticsearch
date: 2019-01-17 11:17:49
categories: 
    - Elasticsearch
tags:
    - 全文搜索
    - SpringBoot
    - Elasticsearch
---



---

原本是采用 transportClient 来写的，但是一个是官方说明在5.x以后的版本就不怎么支持了，二是因为实际环境上使用了加密，无法通过 transportclient 的方式进行查询了，所以综合了一下采用了 High-level-rest-client 的方式。同时在使用 High-level-rest-client 的方式创建 client 的时候务必注意版本的情况，我这里使用的是5.6版本的，不同版本之间创建 client 的方式的差别还是比较大的。



```xml
<!-- https://mvnrepository.com/artifact/org.elasticsearch/elasticsearch -->
<dependency>
    <groupId>org.elasticsearch</groupId>
    <artifactId>elasticsearch</artifactId>
    <version>${org.elasticsearch.version}</version>
</dependency>
<!-- https://mvnrepository.com/artifact/org.elasticsearch.client/transport -->
<dependency>
    <groupId>org.elasticsearch.client</groupId>
    <artifactId>transport</artifactId>
    <version>${org.elasticsearch.version}</version>
</dependency>
```


## 问题：

### 问题详情
```
2019-01-17 15:47:56.134  WARN 45208 --- [ent_boss][T#10]] o.e.transport.netty4.Netty4Transport     : exception caught on transport layer [NettyTcpChannel{localAddress=/127.0.0.1:54984, remoteAddress=/127.0.0.1:9200}], closing connection

io.netty.handler.codec.DecoderException: java.io.StreamCorruptedException: invalid internal transport message format, got (48,54,54,50)
	at io.netty.handler.codec.ByteToMessageDecoder.callDecode(ByteToMessageDecoder.java:472) ~[netty-codec-4.1.30.Final.jar:4.1.30.Final]
	at io.netty.handler.codec.ByteToMessageDecoder.channelInputClosed(ByteToMessageDecoder.java:405) ~[netty-codec-4.1.30.Final.jar:4.1.30.Final]
	at io.netty.handler.codec.ByteToMessageDecoder.channelInputClosed(ByteToMessageDecoder.java:372) ~[netty-codec-4.1.30.Final.jar:4.1.30.Final]
	at io.netty.handler.codec.ByteToMessageDecoder.channelInactive(ByteToMessageDecoder.java:355) ~[netty-codec-4.1.30.Final.jar:4.1.30.Final]
	at io.netty.channel.AbstractChannelHandlerContext.invokeChannelInactive(AbstractChannelHandlerContext.java:245) [netty-transport-4.1.30.Final.jar:4.1.30.Final]
	at io.netty.channel.AbstractChannelHandlerContext.invokeChannelInactive(AbstractChannelHandlerContext.java:231) [netty-transport-4.1.30.Final.jar:4.1.30.Final]
	at io.netty.channel.AbstractChannelHandlerContext.fireChannelInactive(AbstractChannelHandlerContext.java:224) [netty-transport-4.1.30.Final.jar:4.1.30.Final]
	at io.netty.handler.logging.LoggingHandler.channelInactive(LoggingHandler.java:167) [netty-handler-4.1.30.Final.jar:4.1.30.Final]
	at io.netty.channel.AbstractChannelHandlerContext.invokeChannelInactive(AbstractChannelHandlerContext.java:245) [netty-transport-4.1.30.Final.jar:4.1.30.Final]
	at io.netty.channel.AbstractChannelHandlerContext.invokeChannelInactive(AbstractChannelHandlerContext.java:231) [netty-transport-4.1.30.Final.jar:4.1.30.Final]
	at io.netty.channel.AbstractChannelHandlerContext.fireChannelInactive(AbstractChannelHandlerContext.java:224) [netty-transport-4.1.30.Final.jar:4.1.30.Final]
	at io.netty.channel.DefaultChannelPipeline$HeadContext.channelInactive(DefaultChannelPipeline.java:1429) [netty-transport-4.1.30.Final.jar:4.1.30.Final]
	at io.netty.channel.AbstractChannelHandlerContext.invokeChannelInactive(AbstractChannelHandlerContext.java:245) [netty-transport-4.1.30.Final.jar:4.1.30.Final]
	at io.netty.channel.AbstractChannelHandlerContext.invokeChannelInactive(AbstractChannelHandlerContext.java:231) [netty-transport-4.1.30.Final.jar:4.1.30.Final]
	at io.netty.channel.DefaultChannelPipeline.fireChannelInactive(DefaultChannelPipeline.java:947) [netty-transport-4.1.30.Final.jar:4.1.30.Final]
	at io.netty.channel.AbstractChannel$AbstractUnsafe$8.run(AbstractChannel.java:822) [netty-transport-4.1.30.Final.jar:4.1.30.Final]
	at io.netty.util.concurrent.AbstractEventExecutor.safeExecute(AbstractEventExecutor.java:163) [netty-common-4.1.30.Final.jar:4.1.30.Final]
	at io.netty.util.concurrent.SingleThreadEventExecutor.runAllTasks(SingleThreadEventExecutor.java:404) [netty-common-4.1.30.Final.jar:4.1.30.Final]
	at io.netty.channel.nio.NioEventLoop.run(NioEventLoop.java:462) [netty-transport-4.1.30.Final.jar:4.1.30.Final]
	at io.netty.util.concurrent.SingleThreadEventExecutor$5.run(SingleThreadEventExecutor.java:897) [netty-common-4.1.30.Final.jar:4.1.30.Final]
	at java.lang.Thread.run(Thread.java:748) [na:1.8.0_131]
Caused by: java.io.StreamCorruptedException: invalid internal transport message format, got (48,54,54,50)
	at org.elasticsearch.transport.TcpTransport.validateMessageHeader(TcpTransport.java:1072) ~[elasticsearch-6.5.4.jar:6.5.4]
	at org.elasticsearch.transport.netty4.Netty4SizeHeaderFrameDecoder.decode(Netty4SizeHeaderFrameDecoder.java:36) ~[transport-netty4-client-6.5.4.jar:6.5.4]
	at io.netty.handler.codec.ByteToMessageDecoder.decodeRemovalReentryProtection(ByteToMessageDecoder.java:502) ~[netty-codec-4.1.30.Final.jar:4.1.30.Final]
	at io.netty.handler.codec.ByteToMessageDecoder.callDecode(ByteToMessageDecoder.java:441) ~[netty-codec-4.1.30.Final.jar:4.1.30.Final]
	... 20 common frames omitted
```
### 解决方案


---
参考