---
title: 查看class文件的jdk编译版本
date: 2019-02-27 09:55:50
categories: 
    - Java
tags:
    - Java
---



   版本号 |	对应十进制 | jdk版本号
---- | ---- | -------
 2E | 46 | jdk1.2
  2F | 47 | jdk1.3
 30 | 48 | jdk1.4
 31 | 49 | jdk1.5
 32 | 50 | jdk1.6
  33 | 51 | jdk1.7
  34 |  52 | jdk1.8


$f(x) = sinx +1$

Name | Description | Default key binding
-----|-------------|--------------------
md-shortcut.showCommandPalette | Display all commands | ctrl+M ctrl+M
md-shortcut.toggleBold | Make **bold** | ctrl+B
md-shortcut.toggleItalic | Make _italic_ | ctrl+I | 


```flow
st=>start: Start:>http://www.google.com[blank]
e=>end:>http://www.google.com
op1=>operation: My Operation
sub1=>subroutine: My Subroutine
cond=>condition: Yes
or No?:>http://www.google.com
io=>inputoutput: catch something...
para=>parallel: parallel tasks

st->op1->cond
cond(yes)->io->e
cond(no)->para
para(path1, bottom)->sub1(right)->op1
para(path2, top)->op1
```

```sequence{theme="hand"}
Andrew->China: Says Hello
Note right of China: China thinks\nabout it
China-->Andrew: How are you?
Andrew->>China: I am good thanks!
```