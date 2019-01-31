---
title: phpstorm上自动commit
date: 2019-01-29 12:40:02
categories: 
- PHPStorm 
tags: 
- PHPStorm 
- VCS
---

## 场景

代码没有commit, rm -rf 等操作误删了。ctrl+z有时候管用，有时候也很糟心。

## 解决方法

![](/images/15487372770760.jpg)

点击help,搜一下history,很自然的找到vcs下面的show History.

点开可以看见phpstorm保存着一系列记录。

## 结论
1. 当某个功能找不到时，help下面的search极为管用。但简单，但目前为止笔者没看见别人用过。

2. 知道phpstorm有这项功能，vcs全称版本控制服务version control server。

3. IDE的各种功能还是很有必要琢磨一下的！在图形化界面和命令行之间找个平衡点。