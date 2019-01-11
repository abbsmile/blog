---
title: item2操作插入u盘的文件
date: 2019-01-11 08:47:21
categories:
- Mac
tags:
- iTerm2
- MacOS
---

mac上命令行操作的频率远大于界面操作，现在问题来了，插入的u盘、移动硬盘如何用命令行操作。

之前有这么个单词，可是每次用的时候记不住，特意截图一张：

![](https://upload-images.jianshu.io/upload_images/2875232-671827f22644eb24.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

好吧，联系Linux系统上分卷的知识，有点理解了。

再去实际操作一把：

1. 
![](https://upload-images.jianshu.io/upload_images/2875232-191d26b298238c5d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2. 
![](https://upload-images.jianshu.io/upload_images/2875232-df569d8a4f4b02ce.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3. 插入移动硬盘时，发现文件还是在这里面，只是 mac自己电脑的Macintosh HD搞个软链接，这样和其它的一对比，明意上区分开来。

![](https://upload-images.jianshu.io/upload_images/2875232-d6abfcd8664c63f1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

ok, 所有的都是扯淡。。。 `cd /volumes`，，，然后操作，记住这一点，也就够了。

