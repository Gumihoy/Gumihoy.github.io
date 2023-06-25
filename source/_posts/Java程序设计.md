---
title: Java程序设计
date: 2010-09-01 08:01:00
# img: /source/images/xxx.jpg
top: false
hide: false
cover: false
# coverImg: /images/1.jpg
# password: 8d969eef6ecad3c29a3a629280e686cf0c3f5d5a86aff3ca12020c923adc6c92
toc: true
mathjax: false
# summary: 记录Java在Mac系统中的开发环境配置
categories:
    - [Java程序设计]
tags:
    - Java
    - 程序设计
---


> 摘要：汇总Java程序设计，方便后续使用查阅.

## 注释

### 单行注释: //
```java
// 单行注释
```

### 多行注释: /* */
```java
/* 多行注释 */

/*
 * 多行注释
 * 多行注释
 */
```
> /* */ 不能嵌套使用, 必须 /\* 开始, 中介注释, */ 结束

### 文档注释: /** */
自动生成文档
```java
/**
 * 文档注释
 *
 * @author Kent
 */
```

---

## 变量

`变量`就是申请内存来存储的值，当创建`变量`的时候，需要在内存中`申请空间`，`内存管理系统`根据变量的类型为变量分配存储空间，分配的空间只能用来存储该类型的数据

![变量-内存](变量-内存.jpg)

`变量名`必须是一个以`字母`开头并由字母或数字构成的序列, `大小写敏感`。
- 声明
`声明变量`时，`变量`的`类型`位于变量名之前
```java
int i;
float f;
```

- 赋值
```java
i = 0;
f = 0f;
```

> 注意：
> 1. `字母`判断可以使用`Character`类的`isJavaIdentifierStart`和`isJavaIdentifierPart`方法来检查
> 2. 不可以使用`Java保留字`

--- 

## 数据类型
`Java`是`强类型语言`, 分为`基本数据类型(Primitive Type)`、`引用数据类型(Reference Type)`



### 基本数据类型

`8种`基本数据类型

| 项目        | 价格   |  数量  |
| --------   | -----:  | :----:  |
| 计算机     | \$1600 |   5     |
| 手机        |   \$12   |   12   |
| 管线        |    \$1    |  234  |



### 引用数据类型


--- 





## 运算符

## 控制流程


