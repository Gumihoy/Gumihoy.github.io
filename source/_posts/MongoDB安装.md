---
title: MongoDB安装
date: 2018-12-26 10:13:18
tags:
---


https://www.mongodb.com/


## 安装&配置

https://docs.mongodb.com/manual/installation/

### 下载

### 配置


```conf
#数据库路径
dbpath=/Library/mongodb-osx-x86_64-4.0.5/data/

#日志输出文件路径
logpath=/Library/mongodb-osx-x86_64-4.0.5/log/mongodb.log

#错误日志采用追加模式，配置这个选项后mongodb的日志会追加到现有的日志文件，而不是从新创建一个新文件
logappend=true

#启用日志文件，默认启用
journal=true

#这个选项可以过滤掉一些无用的日志信息，若需要调试使用请设置为false
quiet=false

#是否后台启动，有这个参数，就可以实现后台运行
fork=true

#端口号 默认为27017
port=27017

#指定存储引擎（默认不需要指定）
#storageEngine=mmapv1

#开启网页日志监控，有这个参数就可以在浏览器上用28017查看监控界面
httpinterface=true
```

### 启动

```
$ cd bin
$ sudo ./mongod -f /Library/mongodb-osx-x86_64-4.0.5/conf/mongo.conf

about to fork child process, waiting until server is ready for connections.
forked process: 13313
child process started successfully, parent exiting
```

### 关闭
$ cd bin
$ ./mongo
```





## MongoDB可视化界面

### 安装&启动

```bash
sudo git clone https://github.com/mrvautin/adminMongo.git && cd adminMongo
sudo npm install
sudo npm start
```

访问：http://127.0.0.1:1234




<br/>

---

参考

https://github.com/mrvautin/adminMongo
https://adminmongo.markmoffat.com/docs/