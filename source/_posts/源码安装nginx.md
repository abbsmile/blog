---
title: 源码安装nginx
date: 2019-07-18 21:30:19
categories:
- nginx
tags:
- nginx
---

源码安装的灵活性在于随意配置。

我喜欢一个词：信手拈来。有些东西看似随意，其实早已庖丁解牛。编程是要有灵性的，这个灵性，往往来源于从另一个层面看问题。

> 下载

```
http://nginx.org/
```
直接百度下nginx便可得到。我当初在这折腾过一会，然后进去也不知道下载哪个。多试几次就行了。

> 下一步

```
./configure --prefix=/Volumes/mac/basketball/nginx --sbin-path=/Volumes/mac/basketball/nginx/sbin/nginx --conf-path=/Volumes/mac/basketball/nginx/config/nginx.conf --error-log-path=/Volumes/mac/basketball/nginx/logs/error.log --pid-path=/Volumes/mac/basketball/nginx/logs/nginx.pid --http-log-path=/Volumes/mac/basketball/nginx/logs/access.log
```

解压之后这一步蛮重要。配置各种路径什么的，第一次不是瞎蒙就可以的。上面是我的配置，简而言之，记住这几个主要的便可以了。

其实也不用记。尝试运行下下面的命令：
```
./configure --help
```

知道有这么个东西就行。

> 收尾

```
make -j 
make install
```

> 下面是几个常用的命令

```
ps -ef | grep 8823
netstat -nat | grep 8823
 ./nginx -s stop
 ./nginx -s reload
```

如此而已。







