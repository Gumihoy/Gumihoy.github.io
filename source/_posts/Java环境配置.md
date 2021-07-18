---
title: Java环境配置
date: 2021-07-15 18:23:37
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
    - [Java环境配置]
tags:
    - Java
    - Mac
---

> 摘要：汇总Java开发环境配置，方便后续使用查阅.

# Mac环境

## 安装Xcode工具链
新的Mac电脑没有默认安装Xcode工具链，可以在【终端】中通过输入以下命令进行安装：
```bash
xcode-select --install 
```

## OpenJDK安装、配置

### Intel

- #### 安装：方式一
adopt openjdk下载地址：https://adoptopenjdk.net
<br/>
选择openjdk 一个dmg版本下载安装


- #### 安装：方式二（选择一个版本安装）
brew openjdk：(https://formulae.brew.sh/formula/openjdk)

-  安装最新版本
```bash
brew install openjdk
```

- 安装 openjdk 11
```bash
brew install openjdk@11
```

- 安装 openjdk 8
```bash
brew install openjdk@8
```

### Apple M1

Apple M1芯片的macOS可选使用以下aarch64架构的JDK

下载地址：https://cdn.azul.com/zulu/bin/
选择 aarch64.dmg 一个版本下载安装


### 配置
安装完成后，执行下列命令配置JAVA_HOME环境变量，并确认输出的JAVA_HOME指向安装的JDK，以便固定使用此版本的JDK。或者选择手工进行配置
```bash
export JAVA_HOME=$(/usr/libexec/java_home)
echo $JAVA_HOME
test -r ~/.bash_profile && echo "export JAVA_HOME=$JAVA_HOME" >>~/.bash_profile
test -r ~/.profile && echo "export JAVA_HOME=$JAVA_HOME" >>~/.profile
test -r ~/.zshrc && echo "export JAVA_HOME=$JAVA_HOME" >>~/.zshrc
```


## Maven安装、配置

brew maven：https://formulae.brew.sh/formula/maven

```bash
brew install maven
```

## IntelliJ IDEA 配置


---

参考：
- [brew opnejdk](https://formulae.brew.sh/formula/openjdk)
-[brew maven](https://formulae.brew.sh/formula/maven)
- [s](ss)