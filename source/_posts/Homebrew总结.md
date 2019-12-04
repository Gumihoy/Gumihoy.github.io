---
title: Homebrew总结
date: 2015-08-30 08:01:01
categories: 
    - Mac
tags:
    - Mac
    - Homebrew
---

Homebrew是一款Mac OS平台下的软件包管理工具，拥有安装、卸载、更新、查看、搜索等很多实用的功能。简单的一条指令，就可以实现包管理，而不用你关心各种依赖和文件路径的情况，十分方便快捷。

官网：https://brew.sh/index_zh-cn

<!-- more -->


<br/>
## 介绍
Homebrew以Ruby语言写成，针对于Mac OS X操作系统自带Ruby的版本。默认安装在/usr/local，由一个核心git版本库构成，以使用户能更新Homebrew。
包管理器使用一种称为“公式”（formula）的DSL脚本来管理依赖、下载源代码及配置和编译软件，从源代码中构建软件。

Homebrew 会将软件包安装到独立目录，并将其文件软链接至 /usr/local 。
```
cd /usr/local
$ find Cellar
Cellar/wget/1.16.1
Cellar/wget/1.16.1/bin/wget
Cellar/wget/1.16.1/share/man/man1/wget.1
```

<br/>
## 安装(推荐)

```bash
# 查看是否已经安装
brew --version
# 安装
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

<br/>
## 使用
```bash
# 安装指定的软件
brew install <formula>
# 卸载指定的软件
brew uninstall <formula>
# 更新指定的软件
brew upgrade <formula>
# 展示brew安装的所有软件
brew list
# 展示brew信息
brew info
# 检测过时软件
brew outdated
```

## 软件推荐

### 目录树形结构
```bash
# 检查是否安装
$ tree --version
# 安装
$ brew install tree
# 展示目录结构 -N 解决中文乱码
$ tree -N
```

<br/>

---
参考
[官方网站](https://brew.sh/index_zh-cn)