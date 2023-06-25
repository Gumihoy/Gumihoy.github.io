---
title: IntelliJ IDEA破解
date: 2022-02-21 10:52:51
categories: 
    - [IntelliJ IDEA]
tags:
    - IntelliJ IDEA破解
    - 破解
---

> 摘要：汇总`IntelliJ IDEA破解`, 方便后续使用

## 版本大于等于 IntelliJ IDEA 2021.3

> **环境：MacOS**

![破解](1645412947773.jpg)


- 下载 ja-netfilter 最新版本: v2.3.0.zip
```http
https://github.com/ja-netfilter/ja-netfilter/releases
```

解压 放到 `Library`目录下面 `Library/ja-netfilter`

- 下载 ja-netfilter-mymap-plugin 最新版本: v1.2.0.jar
```http
https://github.com/zfkun/ja-netfilter-mymap-plugin/releases
```

放到`Library/ja-netfilter/plugins`目录下面

- 配置

> `ja-netfilter-mymap-plugin`生效配置

在 `Library/ja-netfilter/conf`目录下面创建mymap.conf文件，文件配置如下:

```yaml
# jb 的 mymap.conf 配置文件
[DNS]
EQUAL,jetbrains.com
 
[URL]
PREFIX,https://account.jetbrains.com/lservice/rpc/validateKey.action
 
[MyMap]
EQUAL,licenseeName-> Kent
EQUAL,gracePeriodDays->100000
EQUAL,paidUpTo->5000-12-31
```

> `ja-netfilter.jar`生效配置

打开 `/Help/Edit Custom VM Options` 如图：
![打开Edit Custom VM Options配置文件](1645497394807.jpg)

然后配置`ja-netfilter.jar` 如图：
![ja-netfilter.jar配置](1645497851808.jpg)



### IntelliJ IDEA 2020.2 <= 版本 < IntelliJ IDEA 2021.3
安装`IDE Eval Reset`插件

打开 `Preferences/Plugins` 搜索 `IDE Eval Reset` ，安装

