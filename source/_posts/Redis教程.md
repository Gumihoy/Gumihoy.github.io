---
title: Redis教程
date: 2018-12-05 10:59:05
categories: 
    - Redis
tags:
    - NoSQL
    - Redis
---


Redis 是一个开源（BSD许可）的，内存中的数据结构存储系统，它可以用作数据库、缓存和消息中间件。 它支持多种类型的数据结构，如 `字符串（strings）`， `散列（hashes）`， `列表（lists）`， `集合（sets）`， `有序集合（sorted sets）` 与范围查询， `bitmaps`， `hyperloglogs` 和 地理空间（geospatial） 索引半径查询。 Redis 内置了 复制（replication），LUA脚本（Lua scripting）， LRU驱动事件（LRU eviction），事务（transactions） 和不同级别的 磁盘持久化（persistence）， 并通过 Redis哨兵（Sentinel）和自动 分区（Cluster）提供高可用性（high availability）。


<!-- more -->
---

<br/>

如果自己本地没有安装Redis，可以使用在线Reids。
Redis 在线测试：http://try.redis.io/

<br/>
### 数据类型
Redis支持五种数据类型：`string`（字符串）、`list`（列表）、`hash`（哈希）、`set`（集合）及`zset`(sorted set：有序集合)。


** 1、String（字符串） **
```
redis> SET mykey "Hello"
"OK"
redis> GET mykey
"Hello"
```


** 2、List（列表）** 
```bash
redis> LPUSH mylist "world"
(integer) 1
redis> LPUSH mylist "hello"
(integer) 2
redis> LRANGE mylist 0 -1
1) "hello"
2) "world"
```

列表的最大长度为`2^32 - 1`个元素(`4294967295`，每个列表可容纳超过`40亿`个元素)

** 3、Hash（哈希）**
```bash
redis> HMSET myhash field1 "Hello" field2 "World"
"OK"
redis> HGET myhash field1
"Hello"
redis> HGET myhash field2
"World"
```


** 4、Set（集合）**
```bash
redis> SADD myset "Hello"
(integer) 1
redis> SADD myset "World"
(integer) 1
redis> SADD myset "World"
(integer) 0
redis> SMEMBERS myset
1) "World"
2) "Hello"
```

** 5、ZSET(sorted set：有序集合)**
```bash
redis> ZADD myzset 1 "one"
(integer) 1
redis> ZADD myzset 1 "uno"
(integer) 1
redis> ZADD myzset 2 "two" 3 "three"
(integer) 2
redis> ZRANGE myzset 0 -1 WITHSCORES
1) "one"
2) "1"
3) "uno"
4) "1"
5) "two"
6) "2"
7) "three"
8) "3"
```


### 命令汇总



### 事物



### 发布/订阅

![]()
![]()







<br/>

---
参考
Redis官网：https://redis.io
https://redisbook.readthedocs.io/en/latest/feature/pubsub.html