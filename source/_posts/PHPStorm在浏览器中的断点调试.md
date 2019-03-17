---
title: PHPStorm在浏览器中的断点调试
date: 2018-01-07 22:34:58
categories:
- PHPStorm
tags:
- PHPStorm
---

怎样配置的就不在这里说了，网上教程很多，跟着走就可以了。
可以百度：mac xdebug phpstorm 调试配置

一般要注意两点：
1.Debug port:最好别设置成9000，它默认是9000，但有可能会出错。只要和php.init文件里的配置相同就行了。我设置的是9001
2.localhost有时与127.0.0.1不一样，这个要分清。最好的方法就是一个不行，试试另一个。当然寻根溯源是最好的。

下面是流程：

- 环境
 High Sierra（版本 10.13）  
  XAMPP 7.0.2-1
  ThinkPHP 5

> 设置虚拟域名

我在项目中设置了一个虚拟域名，怎么设置的说不清楚，各种情况都有，要根据问题百度教程相应的教程。大致方向是这三个文件：

` /Applications/XAMPP/xamppfiles/etc/httpd.conf `

打开后，搜索Virtual hosts,定位到这里：
![image.png](http://upload-images.jianshu.io/upload_images/2875232-5db2dd9e4adae6c8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

去掉注释，这样便引用了这个文件，下一个要改的就是这个文件：
```
<VirtualHost *:80>
    DocumentRoot "/Applications/XAMPP/xamppfiles/htdocs/bjzerg/public"
    ServerName a.cn
</VirtualHost>
```
外加上 /etc/hosts 里面配置一下：`127.0.0.1 a.cn` OK.

localhost最好也依样画葫芦配置一下，不然出现的结果有点尴尬。

> PHPStorm中配置

1.PHPStorm右上角
![image.png](http://upload-images.jianshu.io/upload_images/2875232-cfa59997d1d9fb4d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2.添加PHP Web Application
![image.png](http://upload-images.jianshu.io/upload_images/2875232-1e3c161bf73b7c04.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

怎么配置的不要太关心。最好的依据就是中间蓝色的url,这个是关键。

3.PHPStorm右上角有个电话的小按钮：Start Listening for PHP Debug Connections。点击跳转到网页：
![image.png](http://upload-images.jianshu.io/upload_images/2875232-d26e724655f62fc6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)
 
我们要的其实就是箭头所指的东西。

> Postman

下载一个专用的测试url的插件或软件。Postman不错。在url后面加上上图所示的XDEBUG_SESSION_START.在Postman中显示如下图所示：

![image.png](http://upload-images.jianshu.io/upload_images/2875232-96af86d8689485be.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

在PHPStorm中打断点，即可进行调试。


















