---
title: Homebrew
date: 2012-07-15 09:00:00
categories: 
    - [Mac]
    - [Homebrew]
tags:
    - Mac
    - Homebrew
---

> 摘要：记录汇总Homebrew，方便后续使用查阅

Homebrew是一款Mac OS平台下的软件包管理工具，拥有安装、卸载、更新、查看、搜索等很多实用的功能。简单的一条指令，就可以实现包管理，而不用你关心各种依赖和文件路径的情况，十分方便快捷。

官网：https://brew.sh/index_zh-cn

---

## 介绍
`Homebrew`以Ruby语言写成，针对于Mac OS X操作系统自带Ruby的版本。默认安装在`/usr/local`，由一个核心git版本库构成，以使用户能更新Homebrew。
包管理器使用一种称为“公式”（formula）的DSL脚本来管理依赖、下载源代码及配置和编译软件，从源代码中构建软件。

`Homebrew` 会将软件包安装到独立目录，并将其文件软链接至`/usr/local`
```bash
cd /usr/local
find Cellar
```

## 安装
- 查看是否已经安装
```bash
brew -v
```

- 安装(推荐)
```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

## 命令
- 帮助命令
```bash
brew -h
```

- 搜索指定的软件
```bash
brew search <formula>
```

- 安装指定的软件
```bash
brew install <formula>
```

- 卸载指定的软件
```bash
brew uninstall <formula>
```

- 更新指定的软件
```bash
brew upgrade <formula>
```

- 展示brew安装的所有软件
```bash
brew list
```

- 展示brew信息
```bash
brew info
```

- 检测过时软件
```bash
brew outdated
```

## 软件推荐
- Git
```bash
# 检查是否安装
git --version
# 安装
brew install git
```

- wget
```bash
# 检查是否安装
wget --version
# 安装
brew install wget
```

- 目录树形结构
```bash
# 检查是否安装
tree --version
# 安装
brew install tree
# 展示目录结构 -N 解决中文乱码
tree -N
```

---

## 参考
- brew文档：https://docs.brew.sh/