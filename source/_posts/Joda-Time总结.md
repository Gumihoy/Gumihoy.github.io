---
title: Joda Time总结
date: 2019-08-13 19:26:55
tags:
---


官网：https://www.joda.org/joda-time/index.html

为啥用`Joda Time`
- 1. 易于使用:Calendar让获取"正常的"的日期变得很困难，使它没办法提供简单的方法，而Joda-Time能够 直接进行访问域并且索引值1就是代表January。
- 2. 易于扩展：JDK支持多日历系统是通过Calendar的子类来实现，这样就显示的非常笨重而且事实 上要实现其它日历系统是很困难的。Joda-Time支持多日历系统是通过基于Chronology类的插件体系来实现。
- 3. 提供一组完整的功能：它打算提供 所有关系到date-time计算的功能．Joda-Time当前支持8种日历系统，而且在将来还会继续添加，有着比JDK Calendar更好的整体性能等等。
- 



> 大部分人使用`SimpleDateFormat`处理时间格式化过程，但是`SimpleDateFormat`存在并发问题。使用`Joda Time`替代


## 使用

导入jar，地址： https://mvnrepository.com/artifact/joda-time
``` maven
<dependency>
    <groupId>joda-time</groupId>
    <artifactId>joda-time</artifactId>
    <version>2.10.3</version>
</dependency>
```

### `Java`日期对象 与 `Joda Time`日期对象相互转换

#### 毫秒 与 DateTime

**毫秒  =>  DateTime**
```java
long milliseconds = System.currentTimeMillis();
DateTime dateTime = new DateTime(milliseconds);
```

**DateTime  =>  毫秒**
```java
DateTime dateTime = new DateTime();
long milliseconds = dateTime.getMillis();
```


#### Date 与 DateTime

**Date  =>  DateTime**
```java
Date d = new Date();
DateTime dateTime = new DateTime(d);
```

**DateTime  =>  Date**
```java
DateTime dateTime = new DateTime();
Date d = dateTime.toDate();
```


#### Calendar 与 DateTime

**Calendar  =>  DateTime**
```java
Calendar c = Calendar.getInstance();
DateTime dateTime = new DateTime(c);
```

**DateTime  =>  Calendar**
```java
DateTime dateTime = new DateTime();
Calendar c = dateTime.toCalendar(null);
```


### 时间 => 字符串 （时间转换字符串、时间格式化）

**第一种方式** 
```java
Date d = new Date();
DateTime dateTime = new DateTime(d);
dateTime.toString("yyyy-MM-dd HH:mm:ss);
```

**第二种方式** 
```java
Date d = new Date();
DateTime dateTime = new DateTime(d);
DateTimeFormatter formatter = DateTimeFormat.forPattern("yyyy-MM-dd HH:mm:ss");
formatter.print(dateTime);
```


### 字符串 => 时间




### 日期计算

