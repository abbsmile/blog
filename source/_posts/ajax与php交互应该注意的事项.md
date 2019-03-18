---
title: ajax与php交互应该注意的事项
date: 2017-03-19 23:10:14
categories:
- PHP
tags:
- PHP
---

![image.png](https://upload-images.jianshu.io/upload_images/2875232-4f274d8a3aaeea0f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

笔者在公司写php代码时，因为特殊原因，无法使用断点调试。于是，只能用其它调试方法去寻找bug。

正常情况下还好，但每逢遇上ajax与后台php代码交互，笔者一阵心烦气燥。下面总结一下可以用的几种方法。根据不同的情况，灵活运用下面的方法，稍稍可以提高效率：

- 利用`die()`方法。也可以在`die()`中添加字符串，这样可以轻易的判断哪段代码是正确的，哪段代码有点小问题。不足之处是要多次写，多次判断，有点折腾。

- 利用`log`日志。笔者电脑配置：`windows + Oracle VM VirtualBox(CentOS)`。`LAMP`安装在`CentOS`上面。这样，可以在CentOS上直接查看日志，也可以在TP5的log文件里查看日志。`error_log()`外加上php的魔术变量`__LINE__`。不足之处和上面一样，折腾，而且找的过程也纠结。

- 利用浏览器中的`console.log()`以及`Network`中的请求信息，响应信息。这个要配合前面两个方法一起使用。

- 我平时喜欢的方法是直接代入死数据，然后在浏览器中直接写个测试调用控制器的这个方法。代入的死数据可以从浏览器的调试信息中得到。

> 注意：最想说的是这个

笔者调试程序，比较喜欢的语句是`dump()`，因为这个方法对浏览器友好。但是，php代码中如果有这样的语句，ajax通过php获取数据库的流程走不通。笔者在这上面也曾浪费不少时间。


