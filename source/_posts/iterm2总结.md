---
title: iterm2总结
date: 2015-08-30 09:01:01
categories: 
    - Mac
tags:
    - Mac
    - Iterm2
---

iTerm2是Mac终端的替代品，也是iTerm的继承者。 它适用于使用macOS 10.10或更高版本的Mac。

官网：https://www.iterm2.com/index.html

---
<!-- more -->

![iterm2](logo2x.jpg)


<br/>
## 安装

### 下载 
下载地址：https://www.iterm2.com/downloads.html

### 安装
解压文件把iterm2 copy到应用程序


<br/>
## 安装 Powerline 字体
zsh有些主题需要Powerline 字体，Github：https://github.com/powerline/fonts
** 1、安装 **
```bash
git clone https://github.com/powerline/fonts.git --depth=1
cd fonts
./install.sh
cd ..
rm -rf fonts
```
** 2、配置 **
![配置](1543202719106.jpg)


<br/>
## Zsh

https://github.com/robbyrussell/oh-my-zsh/wiki/Installing-ZSH

### Zsh
```bash
# 先查看是否安装
zsh --version
# 安装
brew install zsh zsh-completions
```

<br/>
### Oh My Zsh
** 1、安装 **
```bash
# 安装有两种方式，随意用那种
# curl 安装方式
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

# wget 安装方式
sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```

** 2、配置 **
```
sudo vim ~/.zshrc
```
`修改生效：source ~/.zshrc`

** 3、主题 **
https://github.com/robbyrussell/oh-my-zsh/wiki/themes

Oh My Zsh 默认自带了一些默认主题，存放在 `~/.oh-my-zsh/themes` 目录中。我们可以查看这些主题

```bash
cd ~/.oh-my-zsh/themes
ll
```

```bash
# 打开配置
sudo vim ~/.zshrc
# 配置主题
ZSH_THEME=agnoster
```
`修改生效：source ~/.zshrc`

** 4、卸载 **
```bash
uninstall_oh_my_zsh
```


<br/>
## 配色
![config](1543213263217.jpg)



<br/>

---
参考
[iterm2-官网](https://www.iterm2.com/index.html) 
[oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh/wiki/Installing-ZSH)