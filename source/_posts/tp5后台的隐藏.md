---
title: tp5后台的隐藏
date: 2018-10-10 16:12:35
categories:
- ThinkPHP
tags:
- ThinkPHP
- PHP
- ThinkCMF
- CMS
---

关于这方面的资料，找了很多。还是感觉这个最好：[tp5隐藏后台](http://www.thinkphp.cn/topic/47713.html)

下面稍稍总结一下自己的体会(当然，技术这种东西，面面俱到是不可能的，现在能体会到的是每篇博客只是提供一个大致的方向)：

> 背景

一个cms,内容管理系统，肯定有前端和后台，相对应的是tp5中两个不同的模块。默认情况下，如果网站前台是：test.abble.top，则后台是test.abble.top/admin.

从某种意义上来说，这不安全，显而易见的是暴露了模块名称。

最好的解决方法是：单独为后台设置一个域名。

> 大体主要流程

1. tp5 public目录下面默认有一个入口文件index.php, 可以仿照其样式，再加一个专为进入后台的入口文件admin.php(名字随便起)

![](https://upload-images.jianshu.io/upload_images/2875232-425087f44e92de87.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

如红框所示，这里绑定到了具体的方法。在某种程序上，绑定到相应的模块便可以了。但绑定到相应的模块，如何在配置文件或其它文件中定义默认的控制器和方法，笔者还没搞定，所以只能退而求其次了。

2. nginx中配置虚拟域名

![](https://upload-images.jianshu.io/upload_images/2875232-05e3885b1031ab54.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

如图所示，先定位到public目录下，然后下面是：admin.php。如果你的入口文件是其它文件，则绑定到其它文件。

3. 在路由文件中绑定admin。

tp5的路由文件是：route/route.php,可在里面根据具体的域名绑定模块：
Route::domain('www.abble.top', 'admin');

至于具体的路由，仁者见仁，智者见智了。根据具体的项目，具体问题，具体分析。









