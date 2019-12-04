---
title: Redis安装
date: 2018-12-06 09:19:51
categories: 
    - Redis
tags:
    - NoSQL
    - Redis
---

## MAC环境安装
### 下载
下载地址：http://www.redis.cn/download.html

<br/>
### 安装
```bash
# 进入下载目录 & 解压
$ sudo tar -zxzf redis-xxx.tar.gz
```

<!-- more -->


```bash
# make test
$ sudo make test

[exception]: Executing test client: couldn't execute "src/redis-benchmark": no such file or directory.
couldn't execute "src/redis-benchmark": no such file or directory
    while executing
"exec src/redis-benchmark -p $R_port(0) -n 10000000 -r 1000 incr __rand_int__ > /dev/null &"
    ("uplevel" body line 31)
    invoked from within
"uplevel 1 $code "
    (procedure "start_server" line 3)
    invoked from within
"start_server {} {
    # Config
    set debug_msg 0                 ; # Enable additional debug messages

    set no_exit 0                   ; # Do no..."
    ("uplevel" body line 2)
    invoked from within
"uplevel 1 $code "
    (procedure "start_server" line 3)
    invoked from within
"start_server {} {
start_server {} {
    # Config
    set debug_msg 0                 ; # Enable additional debug messages

    set no_exit 0          ..."
    ("uplevel" body line 2)
    invoked from within
"uplevel 1 $code "
    (procedure "start_server" line 3)
    invoked from within
"start_server {tags {"psync2"}} {
start_server {} {
start_server {} {
    # Config
    set debug_msg 0                 ; # Enable additional debug mess..."
    (file "tests/integration/psync2-reg.tcl" line 7)
    invoked from within
"source $path"
    (procedure "execute_tests" line 4)
    invoked from within
"execute_tests $data"
    (procedure "test_client_main" line 10)
    invoked from within
"test_client_main $::test_server_port "
Killing still running Redis server 48649
Killing still running Redis server 48648
Killing still running Redis server 48663
Killing still running Redis server 48661
Killing still running Redis server 48660
Killing still running Redis server 48856
Killing still running Redis server 48884
Killing still running Redis server 48894
I/O error reading reply
    while executing
"$r bzpopmax $k 2"
    ("uplevel" body line 2)
    invoked from within
"uplevel 1 [lindex $args $path]"
    (procedure "randpath" line 3)
    invoked from within
"randpath {
            $r zadd $k [randomInt 10000] $v
        } {
            $r zadd $k [randomInt 10000] $v [randomInt 10000] $v2
        } {
     ..."
    (procedure "bg_block_op" line 30)
    invoked from within
"bg_block_op [lindex $argv 0] [lindex $argv 1] [lindex $argv 2] [lindex $argv 3]"
    (file "tests/helpers/bg_block_op.tcl" line 52)
I/O error reading reply
    while executing
"$r bzpopmax $k 2"
    ("uplevel" body line 2)
    invoked from within
"uplevel 1 [lindex $args $path]"
    (procedure "randpath" line 3)
    invoked from within
"randpath {
            $r zadd $k [randomInt 10000] $v
        } {
            $r zadd $k [randomInt 10000] $v [randomInt 10000] $v2
        } {
     ..."
    (procedure "bg_block_op" line 30)
    invoked from within
"bg_block_op [lindex $argv 0] [lindex $argv 1] [lindex $argv 2] [lindex $argv 3]"
    (file "tests/helpers/bg_block_op.tcl" line 52)
I/O error reading reply
    while executing
"$r blpop $k $k2 2"
    ("uplevel" body line 2)
    invoked from within
"uplevel 1 [lindex $args $path]"
    (procedure "randpath" line 3)
    invoked from within
"randpath {
            randpath {
                $r rpush $k $v
            } {
                $r lpush $k $v
            }
        } {
            ..."
    (procedure "bg_block_op" line 12)
    invoked from within
"bg_block_op [lindex $argv 0] [lindex $argv 1] [lindex $argv 2] [lindex $argv 3]"
    (file "tests/helpers/bg_block_op.tcl" line 52)
Killing still running Redis server 48948
Killing still running Redis server 48956
Killing still running Redis server 48969
Killing still running Redis server 48975
Killing still running Redis server 49228
Killing still running Redis server 49238
Killing still running Redis server 49251
Killing still running Redis server 49263
Killing still running Redis server 49278
Killing still running Redis server 49295
Killing still running Redis server 49469
Killing still running Redis server 49482
Killing still running Redis server 49501
Killing still running Redis server 49509
Killing still running Redis server 49520
Killing still running Redis server 49535
Killing still running Redis server 49540
Killing still running Redis server 49563
Killing still running Redis server 49566
Killing still running Redis server 49578
Killing still running Redis server 49587
Killing still running Redis server 49648
Killing still running Redis server 49660
make[1]: *** [test] Error 1
make: *** [test] Error 2
```


```bash
# install（上面报错不影响安装）
$ sudo make install

NSTALL redis-sentinel
    CC redis-cli.o
    LINK redis-cli
    CC redis-benchmark.o
    LINK redis-benchmark
    INSTALL redis-check-rdb

Hint: It's a good idea to run 'make test' ;)

    INSTALL install
    INSTALL install
    INSTALL install
    INSTALL install
    INSTALL install
```


### 启动

** 在`Library` 目录创建相应的`redis-xxx`目录 ** 
```bash
$ cd /Library
$ sudo mkdir redis-xxx
```

** 在`redis-xxx`目录下建立`bin`、`conf`、`data`和`log`目录 **

```bash
$ sudo mkdir bin
$ sudo mkdir conf
$ sudo mkdir data
$ sudo mkdir log
```

** 把`make install`之后的`src`目录下的文件 : `mkreleasehdr.sh` `redis-benchmark` `redis-check-rdb` `redis-cli` `redis-server` 拷贝到上面 `bin` 目录 **
```
cp mkreleasehdr.sh /Library/redis-xxx/bin
cp redis-check-rdb /Library/redis-xxx/bin
cp redis-cli /Library/redis-xxx/bin
cp redis-server /Library/redis-xxx/bin
```


```
$ ./redis-server ../conf/redis.conf

$ ./redis-cli

```

### 配置

