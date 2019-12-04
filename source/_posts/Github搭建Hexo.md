---
title: Gihub搭建Hexo
date: 2012-08-01 08:01:01
categories: 
    - Hexo
tags: 
    - Hexo
---

当前教程在Mac上面搭建Hexo

## 环境准备

### Nodejs安装

``` bash
# 测试是否安装
$ node -v
# 如果没有安装，请安装
$ node install
```

<!-- more -->


### Git安装

参考：[Git 安装](/2012/08/01/Mac安装Git)


### Hexo安装

``` bash
# 测试是否安装
$ hexo -v
# 如果没有版本信息，代表没有安装，请按照如下安装Hexo
$ npm install -g hexo-cli
```


## Github搭建Hexo

### 创建Hexo

如果 https://github.com 没有注册账号，先注册: https://github.com/join

在Github创建项目，格式必须要遵守：`账户名.github.io`
创建地址：https://github.com/new

我的账户名：https://github.com/Gumihoy
我的创建项目：`Gumihoy.github.io`

![创建项目](1542073066701.jpg)

``` bash
# 克隆下项目且初始化hexo

$ git clone https://github.com/Gumihoy/Gumihoy.github.io.git
$ hexo init
```

### Hexo 配置

在 `Gumihoy.github.io` 目录修改 `_config.yml`文件
``` yml
# 图片
post_asset_folder: true

# 配置 github项目关联
deploy:
  type: git
  repo: https://github.com/Gumihoy/Gumihoy.github.io.git
  branch: master
```

### 生成静态文件

``` bash
$ hexo g
```

### 启动

``` bash
$ hexo s
```
访问地址： http://127.0.0.1:4000


### 创建分类页
``` bash
$ hexo new page categories
```


### 创建标签页
``` bash
$ hexo new page tags
```


### 创建404页面

``` bash
$ hexo new page 404
```

404内容
``` markdown
---
title: 404 Not Found：该页无法显示
comments: false
permalink: /404
fancybox: false
noDate: "true"
---

<style type="text/css">
	.article-title {
		font-size: 2.1em;
	}
	strong a {
		color: #747474;
	}
	.share {
		display: none;
	}
	.player {
		margin-left: -10px;
	}
	.sign {
		text-align: right;
		font-style: italic;
	}
  	#page-visit {
		display: none;
	}
	.center {
		text-align: center;
		height: 2.5em;
		font-weight: bold;
	}
	.search2 {
		height: 2.2em;
		font-size: 1em;
		width: 50%;
		margin: auto 24%;
		color: #727272;
		opacity: .6;
		border: 2px solid lightgray;
	}
	.search2:hover {
		opacity: 1;
		box-shadow: 0 0 10px rgba(0, 0, 0, 0.3)
		};
	.article-entry hr {
		margin: 0;
	}
	.pic {
		text-align: center;
		margin: 0;
	}
	.pic br {
  		display: none;
  	}
</style>

***

<p class="center">很抱歉，您所访问的地址并不存在: </p>

<p class="center"><a href="/">回主页</a> · <a href="/archives">所有文章</a> · <a href="/about">留言板</a></p>

<p class="center">可在边栏搜索框中对本站进行检索，以获取相关信息。</p>

<div style="text-align: center">
以下是博主喜欢的一些歌曲，可以听听，稍作休息~
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=450 src="https//music.163.com/outchain/player?type=0&id=993980219&auto=1&height=430"></iframe>
</div>
```

### 主题
在theme目录下面执行下面命令
``` bash
git clone https://github.com/Gumihoy/hexo-theme-spfk.git
```
在 `Gumihoy.github.io` 目录下 `_config.yml` 文件修改配置

``` yml
theme: hexo-theme-spfk
```
可以按照上面`生成静态页`、`启动`命令查看主题是否生效


### 评论：gitalk

在`hexo-theme-spfk`目录下面`_config.yml`文件找到 gitalk配置，配置如下
``` yml
gitalk:
  on: true
  owner: gumihoy
  admin: gumihoy
  repo: gumihoy.github.io
  client_id: acedb7865ff08426fa73
  client_secret: f80c2b21236d7eb803d6069c7424de26d957e1bf
```

`client_id`、`client_secret` 可以在Github创建OAuth Apps获取，地址：https://github.com/settings/developers
![OAuth Apps](1542037823098.jpg)

![OAuth Apps配置](1542074055382.jpg)

用自己的 `client_id`、`client_secret` 替换

## Hexo 使用

<br/>
### 创建一个文章

``` bash
$ hexo new xx
```
上面命令会在 `source/_posts`目录下面创建 `xx.md`一个文件，打开`xx.md`可以写文章了

<br/>
### 文章插入图片
在 `Gumihoy.github.io` 目录下 `_config.xml`文件 配置
``` yml
# 图片
post_asset_folder: true
```

按照上面命令创建一个文章，会同时生成一个同样名字的目录，
把文章图片copy到目录中，再在文章引用，如下
`目录下图片文件：1542074055382.jpg；引用：![OAuth Apps配置](1542074055382.jpg)`


<br/>
### 文章摘要设置

在文章插入 `<!-- more -->` ，`<!-- more -->`之前的内容就是摘要




------
参考

[Hexo官方文档](https://hexo.io/zh-cn/docs/)