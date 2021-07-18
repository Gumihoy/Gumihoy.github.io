---
title: Mac 使用rz、sz 远程上传、下载文件
date: 2015-08-30 10:00
categories: 
    - [Mac]
    - [rz]
    - [sz]
tags:
    - Mac
    - rz
    - sz
---

> 摘要：记录`lrzsz`配置、使用，方便后续使用查阅

`lrzsz`是一款在linux里可代替ftp上传和下载的程序。通过它来使用rz，sz

## 安装

- 检查是否安装
```bash
rz --version
sz --version
```

- 安装
```bash
brew install lrzsz
```


## 与iTerm2结合

- 安装automatic zmoderm
```bash
# 切换到 /usr/local/bin 目录
cd /usr/local/bin
## 如果没有安装 wget：brew install wget
wget https://raw.githubusercontent.com/Gumihoy/iterm2-zmodem/master/iterm2-send-zmodem.sh
wget https://raw.githubusercontent.com/Gumihoy/iterm2-zmodem/master/iterm2-recv-zmodem.sh
# 授权
chmod +x /usr/local/bin/iterm2-send-zmodem.sh
chmod +x /usr/local/bin/iterm2-recv-zmodem.sh
```

- 配置iTerm2 trigger

`iTerm2` --> `Profiles` --> `Open Profiles` --> `Edit Profiles`--> `Advanced` --> `Edit Trigger`

```bash
Regular expression      　　Action      　　　　　　　Parameters

\*\*B0100　　　　　　　　Run Silent Coprocess　　/usr/local/bin/iterm2-send-zmodem.sh
\*\*B00000000000000　  Run Silent Coprocess　　/usr/local/bin/iterm2-recv-zmodem.sh
```

![配置图片](122150034707951.png)


> 最后 iTerm2 重启