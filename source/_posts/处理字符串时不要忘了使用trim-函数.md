---
title: 处理字符串时不要忘了使用trim()函数
date: 2017-03-19 23:08:12
categories:
- PHP
tags:
- PHP
---

![image.png](https://upload-images.jianshu.io/upload_images/2875232-9b6f1f5ac7cd3f60.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)

trim() 函数移除字符串两侧的空白字符或其他预定义字符。

[ltrim()](http://www.w3school.com.cn/php/func_string_ltrim.asp "PHP ltrim() 函数") - 移除字符串左侧的空白字符或其他预定义字符
[rtrim()](http://www.w3school.com.cn/php/func_string_rtrim.asp "PHP rtrim() 函数") - 移除字符串右侧的空白字符或其他预定义字符

技术不重要，而是要有意识使用这个函数。笔者今天遇到个bug,查了很长时间没能找出来。最后发现当把字符串截成两半的时候，后面一个字符串多了一个空格。

所以，在使用函数将数组转化成字符串时，要习惯性的使用trim()函数处理得到的每一个字符串。


