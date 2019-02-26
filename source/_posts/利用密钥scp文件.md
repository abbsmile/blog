---
title: 利用密钥scp文件
date: 2019-02-26 20:26:00i
categories: 
- CentOS
tags:
- Linux
- command
- iTerm2
---

## 背景

有个需求，上传文件至服务器(运维提供了`.pem`文件登录)。

同事说`FileZilla`不行，那个必须要输入密码。

于是笔者找了下scp的其它参数，发现还真的可以。

## 解决方案

先看这篇文章，关于登录的：[iTerm2通过pem文件登录
](http://www.abble.top/2019/02/18/iTerm2%E9%80%9A%E8%BF%87pem%E6%96%87%E4%BB%B6%E7%99%BB%E5%BD%95/)

> 1.查看scp命令

```
man scp
```
```
 scp [-i identity_file] [[user@]host1:]file1 ... [[user@]host2:]file2
 
 -i identity_file
             Selects the file from which the identity (private key) for public key authentication is read.This option is directly passed to ssh(1).
```

> 2.执行

把`.pem`文件权限改为600,然后执行：
```
scp -i /Users/abaoooo/.ssh/server.pem -p 22 dist.zip root@111.111.111.111:/var/www/html
```

ok,成功了，又学到一招！命令行中的那些破英语、还有规则什么的，要一个一个啃！



