---
title: Install composer on macOS High Sierra
date: 2018-03-18 23:04:25
categories:
- Composer
tags:
- Composer
---

![KnpU-Composer.png](https://upload-images.jianshu.io/upload_images/2875232-361e8a75973595ab.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)

本地上传图片的过程中，Safari好像比Chrome稍微慢一点。下面说正事

> install composer on macOS

tp5官网上的命令是：
```
curl -sS https://getcomposer.org/installer | php
mv composer.phar /usr/local/bin/composer
```
在实验过程中：`|`后不加空格的话，会理想一点。

两步过后：
```
composer --version
```
如果能看见类似下面的内容，表明安装成功
```
Composer version 1.6.3 2018-01-31 16:28:17
```

> install tp5 via composer

tp5官网上的命令是：
```
composer create-project topthink/think=5.0.* tp5  --prefer-dist
```
照做了，于是，bug重现。我最大的错误在于没有仔细研读后面的错误提示，也没有打断点的思维习惯，一直以为是composer安装失误。所有事后我认为理所当然的事，在事前，也理所当然的没有被我意识到。

最后利用第三方在国内做的全景镜像，下载安装成功：
```
composer config -g repo.packagist composer https://packagist.phpcomposer.com
composer create-project topthink/think tp5
```
其中topthink/think是核心文件，然后tp5是我们起的一个名字。

解决前一个bug靠的是经验，感觉；后一个是隔了一会儿看视频找到了些许灵感，当然简书也提供了帮助。至于搜索引擎，官网，我的首选，这次反而浪费了时间和精力。














