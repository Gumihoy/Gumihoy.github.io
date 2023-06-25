---
title: Git 分布式版本控制系统
date: 2014-08-07 17:34:41
# img: /source/images/xxx.jpg
top: false
hide: false
cover: false
# coverImg: /images/1.jpg
# password: 8d969eef6ecad3c29a3a629280e686cf0c3f5d5a86aff3ca12020c923adc6c92
toc: true
mathjax: false
# summary:
categories:
    - 版本控制系统
tags:
    - 版本控制系统
    - Git
---

> 摘要: 学习`Git`, 从概念、发展脉络、安装、基本使用、分支模型、服务器端配置&使用、分布式工作流、高级命令以及实现细节等


## 基础认识

### 版本控制
一种记录一个或若干文件内容变化，以便将来查阅特定版本修订情况的系统

#### 发展脉络
##### `本地版本控制系统`
补丁方式，重新计算各个版本文件内容。
- `优势`：简单
- `缺点`：单点故障
    
##### `集中化的版本控制`
客服端存储项目最新快照（协同工作）
- `优势`：可以看到项目中的其他人正在做什么。
- `缺点`：服务器单点故障

##### `分布式版本控制系统`
客户端存储项目完整镜像（包括完整历史记录、）（可以定制协作流程）  
- `优势`：无单点故障 
- `缺点`：

### Git
一个分布式控制系统。最开始基于存储Linux项目版本控制

#### Git发展脉络
- 1991~2002: 手动保存归档
- 2002~2005：使用`BitKeeper`来管理和维护代码（后面与`BitKeeper`公司产生冲突，不准Linux使用BitKeeper）
- 2005~：`Linus Torvalds`开发Git代替`BitKeeper`

#### Git设计目标
- 速度
- 简单
- 对非线性开发模式的强力支持（允许成千上万个并行开发的分支）
- 完全分布式
- 管理大规模项目（类似 Linux 内核一样的超大规模项目（速度和数据量）)

#### Git优势&区别
- `数据存储结构`: `直接记录快照，而非差异比较`. 对当时的提交更新的文件创建一个快照并保存这个快照的索引；文件没有修改,只保留一个链接指向之前存储的文件
- `数据提交速度`：`近乎所有操作都是本地执行`
- `数据提交传输完整性`：所有的数据在存储前都计算校验和，然后以校验和来引用。校验和：`SHA-1`算法, 40个十六进制字符（0-9 和 a-f）组成的字符串，基于 `Git` 中文件的`内容`或`目录结构`计算出来
- `持久化不会丢失`：`Git`几乎不会执行任何可能导致文件不可恢复的操作。一般只添加数据，很难从Git删除数据

#### Git状态
- `已提交(committed)`：数据已经安全地保存在本地数据库中
- `已修改(modified)`：修改了文件，但还没保存到数据库中
- `已暂存(staged)`：对一个已修改文件的当前版本做了标记，使之包含在下次提交的快照中

#### Git三个阶段
- `工作区`: 是对项目的某个版本独立提取出来的内容。 这些从 Git 仓库的压缩数据库中提取出来的文件，放在磁盘上供你使用或修改。
- `暂存区`: `暂存区`是一个文件，保存了下次将要提交的文件列表信息，一般在 Git 仓库目录中。 按照 Git 的术语叫做“索引”，不过一般说法还是叫`暂存区`
- `Git 仓库目录`: 是 `Git` 用来保存项目的元数据和对象数据库的地方。 这是 Git 中最重要的部分，从其它计算机克隆仓库时，复制的就是这里的数据。

![Git工作流程](areas.png)
**工作流程：**
- 在工作区中修改文件
- 将你想要下次提交的更改选择性地暂存，这样只会将更改的部分添加到暂存区。
- 提交更新，找到暂存区的文件，将快照永久性存储到 Git 目录。

## Git安装
> macOS 环境
- 安装`Git`
```bash
brew install git
```
- 安装`Git可视化界面`
```bash
brew install git-gui
```

## Git配置
```bash
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```

---

## Git命令使用
### 配置&管理
- 查看Git当前所有配置
```bash
git config --list
```

- 查看Git指定变量配置
```bash
git config user.name
```

- 获取帮助命令
```bash
git help <verb>
git <verb> --help
man git-<verb>
```
如：获取`git config`命令手册
```bash
git help config
```

### 获取仓库
- 将尚未进行版本控制的本地目录转换为`Git 仓库`
```bash
git init
```
- 克隆 一个已存在的`Git 仓库`
```bash
git clone https://github.com/xxx
```

### 本地文件操作
- 查看当前文件状态
```bash
git status
```

- 将内容添加到下一次提交中
```bash
git add .
```

- 提交文件, 产生一次提交记录
```bash
git commit -m 'xx'
```

- 提交文件，向前面提交记录追加文件
```bash
git commit --amend
```

- 删除跟踪，但是保留文件
```bash
git rm --cached README
```

- 查看提交历史
```bash
git log
```

- 查看每次提交的简略统计信息
```bash
git log --stat
```
| 选项	| 说明
|:----:|:---:|
| -p | 按补丁格式显示每个提交引入的差异。
| --stat | 显示每次提交的文件修改统计信息。
| --shortstat | 只显示 --stat 中最后的行数修改添加移除统计。
| --name-only | 仅在提交信息后显示已修改的文件清单。
| --name-status | 显示新增、修改、删除的文件清单。
| --abbrev-commit | 仅显示 SHA-1 校验和所有 40 个字符中的前几个字符。
| --relative-date | 使用较短的相对时间而不是完整格式显示日期（比如“2 weeks ago”）。
| --graph | 在日志旁以 ASCII 图形显示分支与合并历史。


- 按照预订格式:`oneline`、`short`、`full` 和 `fuller` 查看每次提交历史
```bash
git log --pretty=oneline
```

- 按照格式:查看每次提交历史
```bash
git log --pretty="format:"%h - %an, %ar : %s"
```
| 选项	| 说明 |
|:---:|:---:|
| %H | 提交的完整哈希值
| %h | 提交的简写哈希值
| %T | 树的完整哈希值
| %t | 树的简写哈希值
| %P | 父提交的完整哈希值
| %p | 父提交的简写哈希值
| %an | 作者名字
| %ae | 作者的电子邮件地址
| %ad | 作者修订日期（可以用 --date=选项 来定制格式）
| %ar | 作者修订日期，按多久以前的方式显示
| %cn | 提交者的名字
| %ce | 提交者的电子邮件地址
| %cd | 提交日期
| %cr | 提交日期（距今多长时间）
| %s | 提交说明


### 远程仓库
- 查看远程仓库
```bash
git remote -v
```

- 添加远程仓库
```bash
git remote add <shortname> <url>
```

- 从远程仓库中获得数据
```bash
git fetch <remote>
```

- 从远程仓库中获得数据&并自动尝试合并当前分支
```bash
git pull <remote>
```

- 推送到远程仓库
```bash
git push <remote> <branch>
```

- 查看某个远程仓库
```bash
git remote show <remote>
```

- 远程仓库重命名
```bash
git remote rename pb paul
```

- 远程仓库移除
```bash
git remote remove paul
```


### 标签
- 查看标签
```bash
git tag
```

- 查看某个系列标签
```bash
git tag -l "1.8.0"
```

- 创建轻量标签
```bash
git tag v1.4
```

- 创建附注标签
```bash
git tag -a v1.4 -m "version 1.4"
```

- 查询具体标签信息
```
git show v1.4
```

- 推送指定标签
```bash
git push origin v1.4
```

- 推送全部标签
```bash
git push origin --tags
```

- 删除本地标签
```bash
git tag -d v1.4
```

- 删除远程标签
```bash
git tag --delete v1.4
```

### Git别名配置
- 设置别名
```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
```

### 分支管理

- 创建分支
```bash
git branch testing
```

- 切换分支
```bash
git checkout testing
```

- 删除本地分支
```bash
git branch -d testing
```
- 删除远程分支
```bash
git push -delete testing
```

- 修改分支跟踪
```bash
git branch -u origin/serverfix
```

### 分支合并
分支合并有2中方式
- `merge`
- `rebase`
#### Merge
会把两个分支的最新快照以及二者最近的共同祖先（C2）进行三方合并，合并的结果是生成一个新的快照（并提交）
- 分支合并: 把<branch>分支代码合并到当前分支
```bash
git merge <branch>
```
![merge合并](basic-merging-2.png)


- 分支合并冲突解决
合并两个分支，如果有冲突，合并会停止，必须先解决冲突
如：
```html
<<<<<<< HEAD:index.html
<div id="footer">contact : email.support@github.com</div>
=======
<div id="footer">
 please contact us at support@github.com
</div>
>>>>>>> iss53:index.html
```

留下有效代码，把 `<<<<<<<`、`=======`、`>>>>>>>` 移除

#### 变基（rebase）
```bash
git rebase <branch>
```

首先找到这两个分支（即当前分支 experiment、变基操作的目标基底分支 master） 的最近共同祖先 C2，然后对比当前分支相对于该祖先的历次提交，提取相应的修改并存为临时文件， 然后将当前分支指向目标基底 C3, 最后以此将之前另存为临时文件的修改依序应用.
案例：
```bash
git checkout experiment
git rebase master
```

![将 C4 中的修改变基到 C3 上](basic-rebase-3.png)


> `优点`：变基使得提交历史更加整洁, 提交历史是一条直线没有分叉
> `风险`：如果提交存在于你的仓库之外，而别人可能基于这些提交进行开发，那么不要执行变基

## Git服务器
### 协议
Git 可以使用四种不同的协议来传输资料: `本地协议（Local）`、`HTTP 协议`、`SSH（Secure Shell）协议`及 `Git协议`
#### 本地协议
远程版本库就是同一主机上的另一个目录

去克隆一个版本库或者增加一个远程到现有的项目中，使用版本库路径作为 URL
```bash
git clone /srv/git/project.git

## 或者
git clone file:///srv/git/project.git
```

> **优点：**
> - 简单
> - 直接使用了现有的文件权限和网络访问权限
>
> **缺点：**
> - 共享文件系统比较难配置，并且比起基本的网络连接访问，这不方便从多个位置访问
> - 并不保护仓库避免意外的损坏。 每一个用户都有“远程”目录的完整 shell 权限，没有方法可以阻止他们修改或删除 Git 内部文件和损坏仓库

#### HTTP协议
> **优点：**
> - 像 `git:// 协议`一样提供匿名服务
> - 像 `SSH 协议`一样提供传输时的授权和加密
> - 使用比SSH简单
>
> **缺点：**
> - 架设 HTTPS 协议的服务端会比 SSH 协议的棘手一些
> - 管理凭证会比使用 SSH 密钥认证麻烦一些

#### SSH协议
> **优点：**
> - 容易架设
> - 访问安全：所有传输数据都要经过授权和加密
> - 协议很高效: 在传输前也会尽量压缩数据
>
> **缺点：**
> - 不支持匿名访问 `Git` 仓库

#### Git协议
> **优点：**
> - 网络传输协议里最快的
> - 使用与 SSH 相同的数据传输机制，但是省去了加密和授权的开销
>
> **缺点：**
> - 缺乏授权机制
> - 是最难架设的


### 搭建服务器
#### GitLab 


### SSH配置
- 查看用户的 `SSH 密钥`
```bash
$ cd ~/.ssh
$ ls
authorized_keys2  id_dsa       known_hosts
config            id_dsa.pub
```

- 创建`SSH 密钥`
```bash
ssh-keygen -o
```

- 获取公钥&配置公钥
```bash
cat ~/.ssh/id_rsa.pub
```

## Git工作流程

### 集中式工作流
单点协作模型
![集中式工作流](centralized_workflow.png)

### 集成管理者工作流
1. 项目维护者推送到主仓库。

2. 贡献者克隆此仓库，做出修改。

3. 贡献者将数据推送到自己的公开仓库。

4. 贡献者给维护者发送邮件，请求拉取自己的更新。

5. 维护者在自己本地的仓库中，将贡献者的仓库加为远程仓库并合并修改。

6. 维护者将合并后的修改推送到主仓库。

![集成管理者工作流](integration-manager.png)

见于Github平台最常用的工作流程.

### 主管与副主管工作流
多仓库工作流程的变种。 一般拥有数百位协作开发者的超大型项目才会用到这样的工作方式

![主管与副主管工作流](benevolent-dictator.png)


## Git工具
### grep搜索
从提交历史、工作目录、甚至索引中查找一个字符串或者正则表达式.

```bash
git grep <option> <字符串、正则表达式>
```

### 日志搜索
- 想找到 `<搜索>` 是什么时候引入的
```bash
git log -S <搜索> --oneline
```



---

## Git原理&实现
### Git目录结构
- 切换到`.git`目录
```bash
cd .git
```

- Git目录结构
```bash
ls -F1
```
目录:
```bash
COMMIT_EDITMSG
FETCH_HEAD
HEAD
ORIG_HEAD
config
description
hooks/
index
info/
logs/
objects/
packed-refs
refs/
```

- `objects` 目录存储所有数据内容；
- `refs` 目录存储指向数据（分支、远程仓库和标签等）的提交对象的指针； 
- `HEAD` 文件指向目前被检出的分支；
- `index` 文件保存暂存区信息


### 读取文件内容
- 
```bash
git cat-file -p d670460b4b4aece5915caf5c68d12f560a9fe3e4
```



### 存储结构
- `blob对象`：存储文件快照，而不是差异内容
- `tree对象`：记录着目录结构和 blob 对象索引
- `commit对象`：包含指向前述树对象的指针和所有提交信息

![提交对象及其树结构](commit-and-tree.png)

![提交对象及其父对象](commits-and-parents.png)






---
参考
- [Pro Git](https://git-scm.com/book/zh/v2)
- [Git macOS安装](https://git-scm.com/download/mac)
- Git权威指南