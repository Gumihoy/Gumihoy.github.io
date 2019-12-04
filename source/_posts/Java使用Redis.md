---
title: Java使用Redis
date: 2018-12-06 09:22:22
categories: 
    - Redis
tags:
    - NoSQL
    - Redis
---

Redis 支持很多种语言客户端：`ActionScript` `Bash` `C` `C#` `C++` `Clojure` `Common Lisp`  `Crystal`  `D`  `Dart`  `Elixir`  `emacs lisp` `Erlang`  `Fancy`  `gawk`  `GNU Prolog`  `Go`  `Haskell` `Haxe`  `Io`  `Java`  `Javascript`  `Julia`  `Lua` `Matlab`  `Nim`  `Node.js`  `Objective-C`  `OCaml`  `Pascal` `Perl`  `PHP`  `Pure Data`  `Python`  `R`  `Racket` `Rebol`  `Ruby`  `Rust`  `Scala`  `Scheme`  `Smalltalk` `Swift`  `Tcl`  `VB` `VCL`

官网客户端选择：https://redis.io/clients

<!-- more -->
---

<br/>

在Redis官网推荐的Java客户端有`Jedis`、`Lettuce`和`Redisson`。对这三个客户端的介绍如下：

- Jedis：一个非常小而且健全的redis java客户端。
- Lettuce：高级Redis客户端，用于线程安全同步，异步和反应使用。支持群集，哨兵，管道和编解码器。
- Redisson：Redis服务器之上的分布式和可伸缩的Java数据结构。

<br/>
### Jedis
Github：https://github.com/xetorthio/jedis

```xml
<!-- https://mvnrepository.com/artifact/redis.clients/jedis -->

```





<br/>
### Lettuce
Github：https://github.com/lettuce-io/lettuce-core

```xml
<!-- https://mvnrepository.com/artifact/io.lettuce/lettuce-core -->

```



<br/>
### Redisson
Github：https://github.com/redisson/redisson

```xml
<!-- https://mvnrepository.com/artifact/org.redisson/redisson -->


```
