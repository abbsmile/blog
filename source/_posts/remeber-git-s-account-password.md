---
title: remeber git's account & password
date: 2019-01-10 23:12:35
tags:
---

首先，来张图：

![](https://upload-images.jianshu.io/upload_images/2875232-0dab6d6e50e24e51.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

昨天电脑空间不够，清理缓存的时候不小心把git帐号密码全删了。

表现为：git pull时，要重新输入帐号密码。

解决方法：

运行以下代码：
```
git config credential.helper store
```
然后在`git pull`时输入帐号密码，一切都被记住了。

