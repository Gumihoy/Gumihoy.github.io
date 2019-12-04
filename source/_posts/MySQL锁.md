---
title: MySQL锁
date: 2019-06-06 17:56:32
categories:
    - SQL
    - MySQL
tags:
    - SQL
    - MySQL
---



<!-- more -->

---


## InnoDB

### 共享锁（shared (S) lock）和 排它锁（exclusive (X) lock）
InnoDB实现了两种类型的行级锁：
- `共享锁（shared (S) lock）`：允许持有锁的事务读取一行
- `排它锁（exclusive (X) lock）`：允许持有锁的事务更新或删除行

用一张经典的矩阵表格继续说明共享锁和排他锁的互斥关系：

 | S | X
-|---|---
S | 兼容 | 冲突
X | 冲突 | 冲突

- 如果一个事务对某一行数据加了S锁，另一个事务还可以对相应的行加S锁，但是不能对相应的行加X锁。
- 如果一个事务对某一行数据加了X锁，另一个事务既不能对相应的行加S锁也不能加X锁。


<br/>
### 意向锁



 | X | IX | S | IS
-|---|----|---|---
X | 冲突 | 冲突 | 冲突 | 冲突
IX | 冲突 | 兼容 | 冲突 | 兼容
S | 冲突 | 冲突 | 兼容 | 兼容
IS | 冲突 | 兼容 | 兼容 | 兼容


<br/>
### Record Locks



<br/>
### Gap Locks



<br/>
### Next-Key Locks



<br/>
### AUTO-INC Locks



### 加锁语句
- `select ... from`: InnoDB引擎采用多版本并发控制（MVCC）的方式实现了非阻塞读，所以对于普通的select读语句，InnoDB并不会加锁[【备注1】](#备注1)
- `select ... from lock in share mode`: 
- `select ... from for update`: 
- `update ... where ...`: 




---

<br/>
### 备注
<span id="备注1">**【备注1】**: xxxx sffs</span>



---

<br/>

**参考**
[MySQL innodb-locking](https://dev.mysql.com/doc/refman/8.0/en/innodb-locking.html)
《高性能MySQL》
《MySQL技术内幕——InnoDB存储引擎》