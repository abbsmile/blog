---
title: centOS上快速打开指定的mysql数据库
date: 2018-03-09 21:51:30
categories:
- MySQL
tags:
- MySQL
---

在centOS上开发项目时，我们可能会经常打开某个数据库。如何设置，才能确保快速有效地进入数据库？如下所示：

![image.png](https://upload-images.jianshu.io/upload_images/2875232-f75c35d0b588e7a0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

当我们经常使用`ssear`数据库时，只要配置好，输入`mysql`便可快速进入相应数据库。

方法：

1.进入`.my.cnf`文件。这是个隐藏文件，`ls -a`才能看到全部
```
cd ~
vim .my.cnf
```
2.在mysql的配置文件：
```
[mysql]
database = databaseName
user = userName
password = password
```
配置好，重启生效即可。








