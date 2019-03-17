---
title: 在mac上安装thinkcmf
date: 2018-03-07 21:34:25
categories:
- ThinkPHP
tags:
- ThinkPHP
---

![.jpg](http://upload-images.jianshu.io/upload_images/2875232-3ddf4bf1ca4b44e7.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

以前是在CentOS上安装的thinkcmf,记忆中一直很顺利。昨天在mac上安装，遇到点小波折。然后这里记录一下。

1.首先会遇到下面的错误

![image.png](http://upload-images.jianshu.io/upload_images/2875232-5e3f3115ac5c2a86.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/310)

稍加分析，找到`$cacaeFile`所代表的路径，便知道了是权限的问题。

同理，如果改变了这里的权限。接下来会出现这样的错误：

![image.png](http://upload-images.jianshu.io/upload_images/2875232-6f59047bb906689e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/310)

因此，在安装之前，我们可以：`chmod 777 data ./public/upload`改变两个文件夹的权限。以便apache可以对其操作。

2.`下一步`安装的时候，有可能会遇到这样的错误：
![image.png](http://upload-images.jianshu.io/upload_images/2875232-8e662789ba70efee.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/310)

这个时候，我们可以到`httpd.conf`修改`AllowOverride All`,如下所示：
![image.png](http://upload-images.jianshu.io/upload_images/2875232-d90943206a2d417e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/310)

3.我也遇到过这样的问题，不过后来莫名其妙没有了。觉得没有意义。没有深究了。然后在这里，听别人说：必须是root，其它用户不行。这是个bug。

![image.png](http://upload-images.jianshu.io/upload_images/2875232-47a105f027f6a144.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/310)

![image.png](http://upload-images.jianshu.io/upload_images/2875232-5a510a41c7138291.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/130)

> 安装的时候参考了：[ThinkCMF 的部署](https://tech.yj777.cn/thinkcmf-%E7%9A%84%E9%83%A8%E7%BD%B2/)

这篇文章提到了两点，个人感觉很重要：

1.安装完成后把`install`文件夹删除。这个容易忘记。
2.代码不能用root + password方式获取数据库数据。所以要另创建一个用户，然后修改数据库配置文件。

---bug:这个我还没实验好，有点小难度。





















