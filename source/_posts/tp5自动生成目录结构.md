---
title: tp5自动生成目录结构
date: 2018-03-20 23:15:56
categories:
- PHP
tags:
- PHP
---

![](https://upload-images.jianshu.io/upload_images/2875232-e5f3a48e0fdc804e.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

tp5具备自动创建目录的功能。相比于手动创建，命令行下快速操作更有感觉；同时，创建过程中对整体目录的把握会更好。

不足之处是命名空间引用什么的，要自己单独写。IDE如果配置好，在这方面还是占先天优势的。

方法如下：
1、进入安装好的tp5根目录，复制 `build.php` 文件到 `application` 目录下。
2、进入application\build.php文件，根据 `demo` 写上自己需要的目录结构。
3、返回tp5根目录，运行 `php think build` 命令；如果看见success则表示成功，可以进入相应的目录查看；否则，再查看一下这个流程。

注意：tp5官方文档搜 `build` 可以查看类似上面的步骤，可供参考。[自动生成目录结构](https://www.kancloud.cn/manual/thinkphp5/118021)

