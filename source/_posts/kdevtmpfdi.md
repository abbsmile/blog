---
title: kdevtmpfdi
date: 2020-04-08 11:23:15
categories:
- 运维
tags:
- 安全 
---



#### 源由

还在睡眼朦胧中，同事说服务器被挖矿了。`kdevtmpfdi`  cpu使用率接近100%，python爬虫无法工作。

#### 解决

基本是按照网上教程操作的。用下`top`，`cronjob`,`ps` 这些常用命令齐刷刷地看一下。

[处理kdevtmpfsi挖矿病毒](https://blog.csdn.net/u014589116/article/details/103705690)

[Centos7.3防火墙配置](https://www.cnblogs.com/xxoome/p/7115614.html)

当然，多读几篇稿子，多试试不同的方法，总是好的。

#### 核心点

1、安全还是蛮重要的。虽然根据业务衡量，但基本东西还是要跟上；

2、没有服务器监控的，没事多用一些命令查看一下。写文章可以随意，代码不严谨有点尴尬。	