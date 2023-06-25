---
title: gRPC
date: 2022-02-23 11:20:47
# img: /source/images/xxx.jpg
top: false
hide: false
cover: false
# coverImg: /images/1.jpg
# password: 8d969eef6ecad3c29a3a629280e686cf0c3f5d5a86aff3ca12020c923adc6c92
toc: true
mathjax: false
# summary:
categories:
    - gRPC
tags:
    - gRPC
    - RPC
---

> 摘要：`gRPC`是`Google`开发的`远程过程调用`开源框架

## 引言（Introduction）

![](landing-2.svg)

## 概述（Overview）
### 服务定义（Service definition）
`gRPC`一般使用`protocol buffers`来作为`接口定义语言`(`IDL`), 如下：
```Protobuf
service HelloService {
  rpc SayHello (HelloRequest) returns (HelloResponse);
}

message HelloRequest {
  string greeting = 1;
}

message HelloResponse {
  string reply = 1;
}
```

> `gRPC`允许您定义`四种`服务方法：
#### 一元RPC（Unary RPCs）
客户端向服务器发送单个请求并获得单个响应，就像正常的函数调用一样
```Protobuf
rpc SayHello(HelloRequest) returns (HelloResponse);
```

#### 服务器流式RPC（Server streaming RPCs）
客户端向服务器发送请求并获取流以读回一系列消息。客户端从返回的流中读取，直到没有更多消息为止。`gRPC` 保证单个 `RPC` 调用中的消息顺序
```Protobuf
rpc LotsOfReplies(HelloRequest) returns (stream HelloResponse);
```

#### 客户端流式RPC（Client streaming RPCs）
客户端写入一系列消息并将它们发送到服务器，再次使用提供的流。一旦客户端完成了消息的写入，它就会等待服务器读取它们并返回它的响应。`gRPC` 再次保证了单个 `RPC` 调用中的消息顺序。
```Protobuf
rpc LotsOfGreetings(stream HelloRequest) returns (HelloResponse);
```

#### 双向流式RPC（Bidirectional streaming RPCs）
双方使用读写流发送一系列消息。这两个流独立运行，因此客户端和服务器可以按照他们喜欢的任何顺序读取和写入.

例如：服务器可以在写入响应之前等待接收所有客户端消息，或者它可以交替读取消息然后写入消息，或其他一些读取和写入的组合。保留每个流中消息的顺序

```Protobuf
rpc BidiHello(stream HelloRequest) returns (stream HelloResponse);
```


### API使用（Using the API ）
从.proto文件中的服务定义开始，gRPC 提供了生成客户端和服务器端代码的协议缓冲区编译器插件。gRPC 用户通常在客户端调用这些 API，并在服务器端实现相应的 API。
- 在服务端，服务端实现服务声明的方法，并运行一个 gRPC 服务端来处理客户端调用。gRPC 基础架构解码传入请求、执行服务方法并编码服务响应。
- 在客户端，客户端有一个称为存根的本地对象（对于某些语言，首选术语是客户端），它实现与服务相同的方法。然后客户端可以在本地对象上调用这些方法，将调用的参数包装在适当的协议缓冲区消息类型中 - gRPC 会在将请求发送到服务器并返回服务器的协议缓冲区响应之后进行处理。

### 同步与异步
在服务器收到响应之前阻塞的同步 RPC 调用是最接近 RPC 所追求的过程调用抽象的近似值。另一方面，网络本质上是异步的，在许多情况下，能够在不阻塞当前线程的情况下启动 RPC 是很有用的。

大多数语言中的 gRPC 编程 API 有同步和异步两种风格。您可以在每种语言的教程和参考文档中找到更多信息（完整的参考文档即将推出）。

## 架构

## 生命周期
#### 一元RPC（Unary RPCs）

#### 服务器流式RPC（Server streaming RPCs）


#### 客户端流式RPC（Client streaming RPCs）


#### 双向流式RPC（Bidirectional streaming RPCs）

## 使用
### Java
### Go

---

**参考**
- [gRPC文档](https://grpc.io/docs)



