---
title: json_decode && json_encode
date: 2017-11-18 19:30:31
categories:
- 数据格式
tags:
- JSON
---

####JSON 
  - JavaScript Object Notation
  - Notation
      - the activity of representing something by a special system of marks or characters
- JS对象标记，可以理解成和JS对象没有半毛钱关系。这点很重要。
- __下面两点很重要：__
  - JSON本质上是字符串，用' '扩起来的那种；
  - 是一种轻量级的数据交换格式,使用文本格式存储和保存数据；

#### json_decode — Decodes a JSON string
两种情况，一种加参数true,一种没有参数true

![image.png](http://upload-images.jianshu.io/upload_images/2875232-c2c2e986b0f5f115.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![image.png](http://upload-images.jianshu.io/upload_images/2875232-22097ced16854962.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

没有参数则转化为对象；我们可以取对象的第一个数值a得到1；

![image.png](http://upload-images.jianshu.io/upload_images/2875232-234cc00275511ff2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![image.png](http://upload-images.jianshu.io/upload_images/2875232-3e1587e58cf85e58.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
有参数则转化为数组，如上图所示。

#### json_encode — Returns the JSON representation of a value

对value值进行转化，具体问题具体分析。至于转化再转回去，关于对象的，这里面的水也比较深，只有遇到问题具体问题再具体分析了。

