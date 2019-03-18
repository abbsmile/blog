---
title: MySQL Workbench连接数据库
date: 2018-03-26 08:17:59
categories:
- MySQL
tags:
- MySQL
---

![](https://upload-images.jianshu.io/upload_images/2875232-744585fa6abe6020.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


环境：Windows + Oracle Virtualbox + CentOS 7
数据库在CentOS7上，现在想利用 Windows上面的 Workbench 连接 Linux 上的MySQL 

1.依次点击 `Database -> Manage Connections` 打开如下窗口：

![](https://upload-images.jianshu.io/upload_images/2875232-5fd3c12694b68bbf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)

2.按照上图箭头所示，分别填写相应内容。
笔者MySQL安装在Linux上，所以采用  `Standard TCP/IP over SSH` 的连接方式。
![](https://upload-images.jianshu.io/upload_images/2875232-f2be820ece5c6e3f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)

注意：
`MySQL Server Port:3306` Oracle VM VirtualBox 中的端口转发记得配置上：3306 端口。

![](https://upload-images.jianshu.io/upload_images/2875232-f3e6dcda83bf9b5f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)

