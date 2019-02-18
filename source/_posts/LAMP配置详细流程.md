---
title: LAMP配置详细流程
date: 2019-02-18 21:19:08
categories:
- Apache
tags:
- Apache
---

## 场景

笔者配置LAMP的习惯是，随便找个差不多的文档，跟着流程走下去。遇到问题了，再搜索解决。一般不会遇到什么陌生的问题，会用搜索引擎就行。 可能这样比较慢吧，同事建议整理一份差不多的文档，笔者想想也是，每次装环境都像无头苍蝇一样，浪费了不少时间。

刚刚准备整理，又退缩了。还是把今天用到的几个文档放上去吧，再加个注意事项。

## LAMP安装流程

> 流程

- Aapche直接装
- PHP
[CentOS7采用yum方式安装PHP7](https://www.jianshu.com/p/8d54a401ec06)
- Mysql
[Centos7使用yum安装MySQL5.6](https://www.jianshu.com/p/481763139ef2)

> 注意事项：

- 如果不能访问的话，除了防火墙，端口号什么的，注意下配置文件：ServerName localhost:80(不知道有没有用，以后配置时再看下，这里不d在这里钻牛角尖了)

- 问问运维80端口有没有打开，然后有没有加白名单什么的；

- 下面两句话复制上去，以后联系nginx再详细分析下apache和nginx调用PHP的详细流程
 
```
LoadModule php7_module  /etc/httpd/modules/libphp7.so
LoadModule rewrite_module  /etc/httpd/modules/mod_rewrite.so
```

> 最后

好像以前写过配置LAMP的文章，比这个深刻一点，过了个年，配置也忘的差不多了。好吧，感觉这种东西就要不断的总结，然后尝试，即使最后忘了，有了文档和搜索引擎，还是可以很快拿起来。