---
title: Redis设计与实现
date: 2018-12-06 10:19:30
categories: 
    - Redis
tags:
    - NoSQL
    - Redis
---


## 数据结构

`Redis`键值对都是`对象(object)`组成，理解对象所使用的数据结构，你更加好理解和使用`Redis`

下面剖析对象所使用的`数据结构`：`简单动态字符串` `链表` `字典` `跳跃表` `整数集合` `压缩列表` 6种数据结构

<!-- more -->

<br/>
### 简单动态字符串(simple dynamic string, SDS)

#### 源码解析
```c
struct sdshdr {

    // 记录 buf 数组中已使用字节的数量
    // 等于 SDS 所保存字符串的长度
    int len;

    // 记录 buf 数组中未使用字节的数量
    int free;

    // 字节数组，用于保存字符串
    char buf[];
};
```

- `free` 属性的值为 0 ， 表示这个 SDS 没有分配任何未使用空间。
- `len` 属性的值为 5 ， 表示这个 SDS 保存了一个五字节长的字符串。
- `buf` 属性是一个 char 类型的数组， 数组的前五个字节分别保存了 'R' 、 'e' 、 'd' 、 'i' 、 's' 五个字符， 而最后一个字节则保存了空字符 '\0' 。

![](graphviz-72760f6945c3742eca0df91a91cc379168eda82d.png)


#### `SDS`比`C`字符串区别

| C 字符串	| SDS | 
| :--------: | :-----: |
| 获取字符串长度的复杂度为 O(N)  | 获取字符串长度的复杂度为 O(1) |
| API 是不安全的，可能会造成缓冲区溢出 |	API 是安全的，不会造成缓冲区溢出|
| 修改字符串长度 N 次必然需要执行 N 次内存重分配 | 修改字符串长度 N 次最多需要执行 N 次内存重分配 |
| 只能保存文本数据 | 可以保存文本或者二进制数据 |
| 可以使用所有 <string.h> 库中的函数 |	可以使用一部分 <string.h> 库中的函数|


<br/>
### 链表(Linked List)
#### 源码解析
```c

typedef struct listNode {

    // 前置节点
    struct listNode *prev;

    // 后置节点
    struct listNode *next;

    // 节点的值
    void *value;

} listNode;

typedef struct list {

    // 表头节点
    listNode *head;

    // 表尾节点
    listNode *tail;

    // 链表所包含的节点数量
    unsigned long len;

    // 节点值复制函数
    void *(*dup)(void *ptr);

    // 节点值释放函数
    void (*free)(void *ptr);

    // 节点值对比函数
    int (*match)(void *ptr, void *key);

} list;

```

![](graphviz-167adfc2e52e078d4c0e3c8a9eddec54551602fb.png)
![](graphviz-5f4d8b6177061ac52d0ae05ef357fceb52e9cb90.png)


** 特性总结 **
> `双端：` 链表节点带有 prev 和 next 指针， 获取某个节点的前置节点和后置节点的复杂度都是 O(1) 。
> `无环：` 表头节点的 prev 指针和表尾节点的 next 指针都指向 NULL ， 对链表的访问以 NULL 为终点。
> `带表头指针和表尾指针：` 通过 list 结构的 head 指针和 tail 指针， 程序获取链表的表头节点和表尾节点的复杂度为 O(1) 。
> `带链表长度计数器：` 程序使用 list 结构的 len 属性来对 list 持有的链表节点进行计数， 程序获取链表中节点数量的复杂度为 O(1) 。
> `多态：` 链表节点使用 void* 指针来保存节点值， 并且可以通过 list 结构的 dup 、 free 、 match 三个属性为节点值设置类型特定函数， 所以链表可以用于保存各种不同类型的值。



<br/>
### 字典(Dict)
#### 源码解析
```c
typedef struct dictht {

    // 哈希表数组
    dictEntry **table;

    // 哈希表大小
    unsigned long size;

    // 哈希表大小掩码，用于计算索引值
    // 总是等于 size - 1
    unsigned long sizemask;

    // 该哈希表已有节点的数量
    unsigned long used;

} dictht;

typedef struct dictEntry {

    // 键
    void *key;

    // 值
    union {
        void *val;
        uint64_t u64;
        int64_t s64;
    } v;

    // 指向下个哈希表节点，形成链表
    struct dictEntry *next;

} dictEntry;
```

![](graphviz-bd3eecd927a4d8fc33b4a1c7f5957c52d67c5021.png)


<br/>
### 跳跃表(Skip List)
#### 源码解析
```c
typedef struct zskiplistNode {

    // 后退指针
    struct zskiplistNode *backward;

    // 分值
    double score;

    // 成员对象
    robj *obj;

    // 层
    struct zskiplistLevel {

        // 前进指针
        struct zskiplistNode *forward;

        // 跨度
        unsigned int span;

    } level[];

} zskiplistNode;
```

![](graphviz-8fc5de396a5b52c3d0b1991a1e09558ad055dd86.png)


<br/>
### 整数集合(Int Set)
#### 源码解析
```c
typedef struct intset {

    // 编码方式
    uint32_t encoding;

    // 集合包含的元素数量
    uint32_t length;

    // 保存元素的数组
    int8_t contents[];

} intset;
```

![](graphviz-acf7fe010d7b09c5d2500c72eb555863e67ad74f)


<br/>
### 压缩列表(Zip List)
#### 源码解析
```c

```


## 过期（Expires）

<!-- more -->


## LRU

** 1、需要设置最大内存限制，如：**
```bash
maxmemory 100mb
```

** 2、选择策略 **
```bash
maxmemory-policy noeviction
```


<br/>
### Redis淘汰机制(Eviction policies)

`noeviction`: 默认策略，不淘汰，如果内存已满，添加数据报错。 
`allkeys-lru`: 在所有键中，选取最近最少使用的数据抛弃。
`volatile-lru`: 在设置了过期时间的所有键中，选取最近最少使用的数据抛弃。
`allkeys-random`: 在所有键中，随机抛弃。
`volatile-random`: 在设置了过期时间的所有键，随机抛弃。
`volatile-ttl`: 在设置了过期时间的所有键，抛弃存活时间最短的数据。




![LRU Comparison](lru_comparison.png)



<br/>

---
参考
Redis官网：https://redis.io
《Redis设计与实现》：http://redisbook.com/