---
title: foreach()中加了取地址符&引起的错误
date: 2019-01-11 14:39:08
categories:
- PHP
tags:
---

这个还是比较好玩的，对取地址符也能加深认识。

原文是：# [php的foreach中使用取地址符，注意释放](https://www.cnblogs.com/firstForEver/p/5201618.html)


代码：

![](https://upload-images.jianshu.io/upload_images/2875232-5e1026983f572d71.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

运行结果：

![](https://upload-images.jianshu.io/upload_images/2875232-739511425449f3e6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

1: 第一个foreach()循环后，因为没有释放`$value`, 所以`&$value`是存在的，这个地址指向数组的第三个元素。

2:第二个foreach()循环时，每次给$value赋值，相当于给数组的第三个值赋值。

我的理解中，`unset($value)`，相当于把`&$value`这个地址给毁了。所以在这个程序中是必要的。

结束！




