---
title: 源码安装swool
date: 2019-07-13 20:37:36
categories:
- PHP
tags:
- swoole
---

源码安装swoole，很简单，也很好玩。跟着我的步骤，几步就安装好了，相信我。

首先进入swoole，下载源码。码云下载就可以了，master分支。

进入swoole根目录，运行phpize:这是一个用来扩展PHP扩展模块的工具！通过phpize,我们可以建立php的外挂模块！

接下来运行.config文件：
```
./configure --with-php-config=/Volumes/mac/basketball/php/bin/php-config
```

最后，make && make install 

运行完，进入php的扩展文件夹，会发现swoole.so已存在。后面只要在php.ini文件中加上这个扩展就可以了。

想验证是否安装好，可以用：php -m命令。

另外加一句：软件什么的，对于初学者，最好用源码安装。出了问题心里有数，不用担惊受怕。

结束！

