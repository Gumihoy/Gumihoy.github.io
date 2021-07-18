---
title: iTerm2
date: 2012-07-15 10:00:00
categories: 
    - [Mac]
    - [iTerm2]
tags:
    - Mac
    - Iterm2
---

> 摘要：记录汇总iTerm2配置、使用，方便后续查阅使用

iTerm2 是 Terminal 的替代品，也是 iTerm 的继承者。 它适用于装有 macOS 10.14 或更新版本的 Mac。 iTerm2 将终端带入现代，具有您从未想过的功能。

官网：https://www.iterm2.com/index.html

![iTerm2](logo2x.jpg)

---


## 下载&安装
下载地址：https://iterm2.com/downloads.html
把`iTerm`移动到应用程序中

## 配置
- 设置`iTerm2`为默认终端
![设置iTerm2为默认终端](Setting_Default_Term.png)
点击【`iTerm2` - `Make iTerm2 Default Term`】

- 设置 `Status Bar`
![Status Bar配置](Status_bar.jpg)
点击【`iTerm2` - `Preferences` - `Profiles` - `Session` - `configure Status Bar`】 移到`Active Components`, 也可以移出

- 设置`Theme` & `Status bar location`
![Theme设置](Appearance.jpg)
点击【`iTerm2` - `Preferences` - `Appearance`】配置自己喜欢的`Theme` & `Status bar location`

- 设置颜色
![config](1543213263217.jpg)

## 高级功能
### Zsh

一般终端默认的`Shell`都是`Bash`，但是`Zsh`的功能要多得多。拥有语法高亮，命令行tab补全，自动提示符，显示Git仓库状态等非常强大的功能。

查看当前终端使用`Shell`类型
```bash
echo $SHELL
```

查看当前系统有多少种`Shell`类型
```bash
cat /etc/shells
```

**Zsh安装&切换**
- 先查看是否安装
```bash
zsh --version
```

- 安装（推荐）
```bash
brew install zsh
```
- 更新
```bash
brew upgrade zsh
```

- 切换zsh
```bash
# Recent Mac OS versions
chsh -s /usr/local/bin/zsh
# Mac OS High Sierra and before
chsh -s /bin/zsh
```


### Oh My Zsh
`Oh My Zsh`是一个令人愉快的开源社区驱动工具，用于管理您的 `Zsh` 配置。 它捆绑了数以千计的有用功能、助手、插件、主题和一些让人惊奇的东西：https://ohmyz.sh/

#### 1、安装

https://github.com/robbyrussell/oh-my-zsh/wiki/Installing-ZSH

安装有多种方式，随意用那种

- curl 安装方式（推荐）
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```
- wget 安装方式
```bash
sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```

- fetch 安装方式
```bash
sh -c "$(fetch -o - https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

#### 2、配置

##### 主题
`Oh My Zsh` 默认自带了一些默认主题，存放在 `~/.oh-my-zsh/themes` 目录中。我们可以查看这些主题
```bash
cd ~/.oh-my-zsh/themes
ll
```

> `Oh My Zsh`的 GitHub Wiki 页面提供了主题列表：https://github.com/robbyrussell/oh-my-zsh/wiki/themes

- 打开配置
```bash
sudo vim ~/.zshrc
```
- 配置主题：选择一个你喜欢的，我这里设置随机
```bash
ZSH_THEME="random"
```
- 修改生效
```bash
source ~/.zshrc
```

##### 插件

`Oh My Zsh`的 GitHub Wiki 页面提供了插件列表：https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins

- 查看当前默认安装的插件
```bash
cat ~/.oh-my-zsh/plugins
```
- 查看当前安装的自定义插件
```bash
cat ~/.oh-my-zsh/custom/plugins
```

- 打开配置
```bash
sudo vim ~/.zshrc
```

- **git**：提供了许多别名和一些有用的功能
```bash
plugins=(git)
```
这个是装好`Oh My Zsh`就默认已经开启的，可以查看所有的`git`命令`alias`
```bash
cat ~/.oh-my-zsh/plugins/git/git.plugin.zsh
```
> git plugins: https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/git


- **自动提示**
```bash
# 安装插件(安装在自定义插件目录下面)
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```
```bash
# 插件配置
plugins=( 
    # other plugins...
    zsh-autosuggestions
)
```
> Zsh自动提示 plugins: https://github.com/zsh-users/zsh-autosuggestions

- **高亮**
```bash
# 安装插件(安装在自定义插件目录下面)
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```
```bash
# 插件配置
plugins=( 
    # other plugins...
    zsh-syntax-highlighting
)
```
> Zsh高亮 plugins: https://github.com/zsh-users/zsh-syntax-highlighting


- **vscode**
```bash
# 插件配置
plugins=( 
    # other plugins...
    vscode
)
```
这个是装好`Oh My Zsh`就默认安装了`vscode plugins`，只需要配置
> vscode plugins: https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/vscode

- **sublime**
```bash
# 插件配置
plugins=( 
    # other plugins...
    sublime
)
```
这个是装好`Oh My Zsh`就默认安装了`sublime plugins`，只需要配置
> sublime plugins: https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/sublime



#### 3、卸载
如果想卸载 `Oh My Zsh`,执行下面命令
```bash
uninstall_oh_my_zsh
```


### Powerline 字体
`Zsh`有些字体乱码，主题需要 `Powerline` 字体，Github：https://github.com/powerline/fonts
- **1、安装**
```bash
# clone
git clone https://github.com/powerline/fonts.git --depth=1
# install
cd fonts
./install.sh
# clean-up a bit
cd ..
rm -rf fonts
```
- **2、配置**
![配置](1543202719106.jpg)



---
## 参考
- iterm2-官网：https://www.iterm2.com/index.html
- oh-my-zsh：https://github.com/robbyrussell/oh-my-zsh/wiki/Installing-ZSH