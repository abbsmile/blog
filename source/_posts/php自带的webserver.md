---
title: php自带的webserver
date: 2018-03-22 20:16:24
categories:
- ThinkPHP
tags:
- ThinkPHP
---

![](https://upload-images.jianshu.io/upload_images/2875232-6f05015d382b9b60.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)

笔者不喜欢这样的学习方式：认识一个命令，然后把它的大部分用法学一下。理由很明确：其一枯燥，其二不知所为何用，其三笔者学习能力尤其记忆能力比较差。

笔者同时深知，学习方法只是因时因人因阶段而异，没有所谓的好与坏。上面的学习方式，在某个阶段，对于笔者而言还是有用的。只是，今天这篇文章思路不是这样，它以流程目的为主导。

插个题外话：大学有个同学，跟我讲过同样的学习方法。很荣幸认识这样的人，给我以启迪；很庆幸现在自己还记得。发现别人的优点，然后去学习。三人行，必有我师。

> webserver

__router.php用于php自带webserver支持，可用于快速测试__

LAMP是php web开发的标配，但php自带的webserver在测试环境中可以取代Apache（不建议这样做，毕竟Apache安装配置很简单,而且好用）。

运行一条看似简单的命令即可：
```
➜  public pwd
/Applications/XAMPP/xamppfiles/htdocs/tp5/public
➜  public php -S localhost:8888 router.php
PHP 7.0.13 Development Server started at Thu Mar 22 00:47:46 2018
Listening on http://localhost:8888
Document root is /Applications/XAMPP/xamppfiles/htdocs/tp5/public
Press Ctrl-C to quit.
```
1、端口号可以随意指定，一般情况下取大一点，不可以与本机已有的端口号重复。具体范围可以百度。但大于2000的四位数肯定可以。不建议8080，一般8080的端口号已被占用。

2、可以观察上面的提示，`webserver` 的根目录在 `public` 目录下面，而笔者`Apache`中配置的根目录只到`htdocs`下面。所以访问tp5时，利用Apache服务器时路径还要加上：`/tp5/public`，而在`webserver`直接输入`localhost:8888` 便可直接访问。

> 如何退出？

在讨论退出之前，我们先证明 `8888` 端口已启用。 

两个方法：
1.浏览器直接访问：`localhost:8888` , 可以进入系统，则表示已启用;
2.利用 `ps` 命令

下面问题来了，什么是 `ps` 命令？
`Reports a snapshot of the status of currently running processes.`
`ps` 命令能够给出当前系统中进程的快照。它能捕获系统在某一事件的进程状态。

```
➜  tp5 ps
  PID TTY           TIME CMD
18264 ttys000    0:00.98 /bin/zsh --login -i
22549 ttys000    0:00.10 php -S localhost:8888 router.php
19517 ttys001    0:00.79 /bin/zsh --login -i
```

PID: 进程号 process ID
TTY: 命令所运行的位置 teletypewriters（了解这个要稍微百度一下历史）
TIME: 运行这个命令 cpu 所占用的处理时间 time
CMD: 进程所运行的命令 command

利用`ps`命令看见 `8888` 端口已被启用。

退出进程，两个方法：
1、ctrt + c
2、kill PID (这里是kill 22549)




