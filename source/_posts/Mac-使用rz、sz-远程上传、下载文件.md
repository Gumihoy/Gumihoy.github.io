---
title: Mac 使用rz、sz 远程上传、下载文件
date: 2015-08-30 10:00
categories: 
    - Mac
tags:
    - Mac
---



## 下载安装lrzsz
**安装** 
```bash
sudo brew install lrzsz
```

**建立软连接** 
```
ln -s /usr/local/Cellar/lrzsz/0.12.20/bin/sz
ln -s /usr/local/Cellar/lrzsz/0.12.20/bin/rz
```



## 下载并安装automatic zmoderm
```bash
/usr/local/bin

## 如果没有安装 wget：brew install wget
sudo wget https://raw.github.com/mmastrac/iterm2-zmodem/master/iterm2-send-zmodem.sh
sudo wget https://raw.github.com/mmastrac/iterm2-zmodem/master/iterm2-recv-zmodem.sh

sudo chmod 777 /usr/local/bin/iterm2-*
```


## 添加iTerm2 trigger
```
iTerm2 --> Profiles --> Open Profiles --> Edit Profiles --> Advanced --> Edit Trigger

Regular expression      　　Action      　　　　　　　Parameters

\*\*B0100　　　　　　　　Run Silent Coprocess　　/usr/local/bin/iterm2-send-zmodem.sh
\*\*B00000000000000　  Run Silent Coprocess　　/usr/local/bin/iterm2-recv-zmodem.sh
```


![配置图片](122150034707951.png)


> 最后 iTerm2 重启