---
title: LaTeX教程
date: 2012-09-02 09:01:01
categories:
    - LaTeX
tags:
    - LaTeX
    - 公式
---


LaTeX，是一种基于TEX的排版系统，由美国计算机科学家莱斯利·兰伯特在20世纪80年代初期开发，利用这种格式系统的处理，即使使用者没有排版和程序设计的知识也可以充分发挥由TEX所提供的强大功能，不必一一亲自去设计或校对，能在几天，甚至几小时内生成很多具有书籍品质的印刷品。对于生成复杂表格和数学公式，这一点表现得尤为突出。因此它非常适用于生成高印刷质量的科技和数学、物理文档。这个系统同样适用于生成从简单的信件到完整书籍的所有其他种类的文档。

　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　—————摘自《维基百科》


<!-- more -->

<br/>

---

<br/>

LaTeX 公式 必须要用 `$...$` 或者 `$$...$$` 包裹

`$...$` 、`$$...$$` 区别：`$...$` 排版在左边，`$$...$$` 排版在中间，如：

``` markdown
$H(X)=-\sum_{i=0} P(X_{i}) \log_b P(X_{i})$
```
$H(X)=-\sum_{i=0} P(X_{i}) \log_b P(X_{i})$


<br/>

``` markdown
$$H(X)=-\sum_{i=0} P(X_{i}) \log_b P(X_{i})$$
```
$$H(X)=-\sum_{i=0} P(X_{i}) \log_b P(X_{i})$$


<br/>

### 分数 \frac{a}{b}

``` bash
# a：分子，b：分母
$\frac{a}{b}$
```
$$【例】\frac{a}{b}$$

<br/>
### 指数 a^{b}

``` bash
$a^{b}$
```


<br/>
### 根号 \sqrt{a}
``` bash
$\sqrt{a}$
```



<br/>
### 根号 \sqrt[n]{a}
``` bash
$\sqrt[n]{a}$
```


<br/>
### 极限 \lim\limits_{x \to \infty}
``` bash
$\lim\limits_{x\to\infty}$
```
$【例】\lim\limits_{x \to 0}$
$【例】\lim\limits_{x \to \infty}$


<br/>
### 对数 \log_{b}{a}
``` bash
$\log_{b}{a}$
```
$【例】\log_{b}{a}$

<br/>
### 和 \sum \limits_{n=0}^{\infty}
``` bash
$\sum \limits_{n=0}^{\infty}$
```
$【例】\sum \limits_{n=0}^{\infty}$



<br/>
### 和 \prod \limits_{n=0}^{\infty}
``` bash
$\prod \limits_{n=0}^{\infty}$
```
$【例】\prod \limits_{n=0}^{\infty}$



<br/>
### 和 \int_{a}^{b}
``` bash
$\int_{a}^{b}$
```
$【例】\int_{a}^{b}$




<br/>
### 和 \int_{a}^{b}
``` bash
$\int_{a}^{b}$
```


br/>
### 函数定义 \begin{cases} xx & 描述 \\\ 0 & 描述 \end{cases}
``` bash
\begin{cases} xx & 描述 \\\ 0 & 描述 \end{cases}
```
$【例】\begin{cases} xx & 描述 \\\ 0 & 描述 \end{cases}$

---
参考

[mathjax-basic-tutorial-and-quick-reference](https://math.meta.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference)
[mathjax-latex-basic-tutorial-und-referenz-deutsch](https://www.mathelounge.de/509545/mathjax-latex-basic-tutorial-und-referenz-deutsch)
[在线编辑LaTeX](https://www.matheretter.de/rechner/latex/)