---
title: tensorflow教程
date: 2018-11-22 17:42:36
categories: 
    - Tensorflow
tags:
    - 机器学习
    - 深度学习
    - 深度学习框架
    - Tensorflow
---

TensorFlow™ 是一个开放源代码软件库，用于进行高性能数值计算。借助其灵活的架构，用户可以轻松地将计算工作部署到多种平台（CPU、GPU、TPU）和设备（桌面设备、服务器集群、移动设备、边缘设备等）。
TensorFlow™ 最初是由 Google Brain 团队（隶属于 Google 的 AI 部门）中的研究人员和工程师开发的，可为机器学习和深度学习提供强力支持，并且其灵活的数值计算核心广泛应用于许多其他科学领域。

　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　———摘自《tensorflow.google.cn》

<!-- more -->


![tensors_flowing](tensors_flowing.gif)
<br/>

## 安装
官网：https://tensorflow.google.cn/install/

现在tensorflow在以下系统进行测试和支持：
- Ubuntu 16.04 or later
- Windows 7 or later
- macOS 10.12.6 (Sierra) or later (no GPU support)
- Raspbian 9.0 or later

tensorflow有多种安装方式:
- [Pip 安装](https://tensorflow.google.cn/install/pip)
- [Docker 安装](https://tensorflow.google.cn/install/docker)
- [从源代码安装](https://tensorflow.google.cn/install/source)


本教程使用 pip 在MAC系统的安装方式：https://tensorflow.google.cn/install/pip

<br/>
### MacOS
** 1、安装python、pip、virtualenv **

`要求 Python 3.4, 3.5, or 3.6`

```bash
python3 --version
pip3 --version
virtualenv --version
```

```bash
# 升级pip
sudo python3 -m pip install -U pip

# 安装virtualenv
sudo pip3 install -U virtualenv  # system-wide install
```

** 2、安装 tensorflow（CPU 版） **
`Tensorflow 已经不再支持 mac 的 GPU 版了`
```
# python 3+ 的用户:
$ pip3 install --upgrade tensorflow

# 删除tensorflow原有的版本
$ pip3 uninstall tensorflow
```

** 3、验证Tensorflow是否安装成功 **
在python编译器运行下面代码：
```
import tensorflow as tf
print(tf.__version__)
```


<br/>
## 教程





<br/>

---
参考
[tensorflow官网](https://tensorflow.google.cn/)
[tensorflow官网例子](https://www.tensorflow.org/tutorials/)
http://www.tensorfly.cn/tfdoc/get_started/introduction.html
https://morvanzhou.github.io/tutorials/machine-learning/tensorflow
