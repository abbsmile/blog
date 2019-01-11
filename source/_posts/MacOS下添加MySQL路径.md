---
title: MacOS下添加MySQL路径
date: 2019-01-10 23:57:44
categories:
- Mac
tags:
- MacOS
- MySQL
- Shell
---

这篇文章讲得很清楚。
[MacOS下添加MySQL路径](https://blog.csdn.net/chenkangqiang/article/details/56677541) 

想强调的有两点：

1. `.bash_profile`的通用格式：export PATH=$PATH:路径名 
之前在网上看见其它的格式，笔者电脑系统为：10.13.4 经测试，目前这种格式是可以的。

2. `open -e .bash_profile`
个人感觉这个命令可以一记。

其一：文本编辑，text格式，在系统编辑中经常使用到。但mac中新建文本文件，包括打开很不方便。

其二：按照这种方式，可以很方便的指定利用什么软件打开某一文件。很灵活。

结束！


