---
title: PHP魔术变量
date: 2018-02-28 23:50:47
categories:
- PHP
tags:
- PHP
---


```
__LINE__  // 显示文件中的当前行号
```
![image.png](http://upload-images.jianshu.io/upload_images/2875232-63251b17e9f790b5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


```
__FILE__ // 代码在被包含文件中，显示的是包含文件名的绝对路径 
```
![image.png](http://upload-images.jianshu.io/upload_images/2875232-9e0101b16cd4c6b2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

```
__DIR__ // 代码在被包含文件中，显示的是此文件的绝对目录
```
![image.png](http://upload-images.jianshu.io/upload_images/2875232-7ae3e1039be19197.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

```
这两个比较有意思
__FUNCTION__
__METHOD__
```
![image.png](http://upload-images.jianshu.io/upload_images/2875232-e8823ede6f2d6760.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

```
如果再加两个
__CLASS__
__NAMESPACE__

method和class在我意料之外。
```
![image.png](http://upload-images.jianshu.io/upload_images/2875232-c0e3faa25722ff5f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这些东西没什么大用，但就像一个个螺丝钉一样，一颗一颗把它拧紧。在测试，或者用到图片文件地址时，不失为实用工具。














