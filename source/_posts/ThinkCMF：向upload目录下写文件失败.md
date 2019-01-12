---
title: ThinkCMF：向upload目录下写文件失败
date: 2019-01-12 12:28:38
categories:
- ThinkPHP
tags:
- PHP
- CentOS
- MacOS
- ThinkPHP
- ThinkCMF
- 权限
---

先上一张截图：

![弃我去者，昨日之日不可留；](http://upload-images.jianshu.io/upload_images/2875232-7d49ad64a3ccfd3e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

在服务器，上传图片之类，往往会因为没有写的权限而失败。如上图所示，ThinkCMF里public/upload目录下的headquarters文件夹详细信息里有个bbao。问题的核心就在这bbao上面，一般改成apache就可以了。为什么改成apache就可以了，以后再专门分析，今天先探讨一下权限的基本知识。

下面我们详细分析一下权限的问题：

- ll命令

![乱我心者，今日之日多烦忧](http://upload-images.jianshu.io/upload_images/2875232-b21f8357711ad50a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

从上图可以看出，ls -l 与 ll命令的效果是一样的。ll并不是Linux下的一个基本命令，只是一个别名。`ls --help`查看命令看到这样一条信息。

![image.png](http://upload-images.jianshu.io/upload_images/2875232-4afc903c25620117.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

用`man ls`列出的是英文，我们来看看英文解释：

![image.png](http://upload-images.jianshu.io/upload_images/2875232-c68bfc35c7377047.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

 listing本身有列表的意思，翻译成像表格一样，更有味道。毕竟列出来的东西，有种表格的那种listing味道。题外话了。

而man则是手册的意思，以前为了记这个命令就想像成有了问题问我们男人。现在要改改了,manual。还是要专业，别人问起来的时候不好解释。当然，题外话了……

- ll命令结果说明
`drwxrwxrwx 1 bbao developer 288 10月 23 14:21 headquarters`

 - 第一个栏位`drwxrwxrwx`:表示文件的属性。
Linux中文件属性要分为三种：可读，可写，可执行。
共有10位，可理解为每位为1bit.(1Byte = 8bit中的bit)

__第一个字母表示文件类型：__

![l表示符号链接。可以理解成快捷方式一样的文件，会以l表示。](http://upload-images.jianshu.io/upload_images/2875232-db7da2a55fc255bd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![d表示目录，directory](http://upload-images.jianshu.io/upload_images/2875232-52c490a856ec630b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![-表示一般的文件](http://upload-images.jianshu.io/upload_images/2875232-b9b804d17243cbd2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![c:字符设备文件；b:块设备文件](http://upload-images.jianshu.io/upload_images/2875232-d5b2e7e43c494e56.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)

什么是字符设备文件？什么是块设备文件？

百度百科上的：
字符设备是指在I/O传输过程中以字符为单位进行传输的设备，例如键盘，打印机等。
块设备是i/o设备中的一类，是将信息存储在固定大小的块中，每个块都有自己的地址，还可以在设备的任意位置读取一定长度的数据，例如硬盘,U盘，SD卡。

__第2到第10个字符分别表示不同角色所拥有的权限__
r-read | w-write | e-execute
owner 文件所有者
group 所属组
others 其它 

  - 第二个栏目表示：文件的硬链接数量。
这个暂时没弄清楚。有机会补充。

  - 第三个栏目表示：文件所属都。owner或是user 好像都有那种味道

  - 第四个栏目表示：文件所属用户组 group

  - 第5个栏目表示： 文件大小，比如 480 表示 480Byte. 这个要注意Byte的B要大写。1Byte = 8bit 要有规范意识，一是专业，二是方便以后的学习。

     这里可以提一下我很长时间的误区。1KB = 1024Byte 上学的时候，我一看见K就自动翻译成1000了。没有把加入到这个大家庭中去。

 - 第6个栏目表示：最新的修改时间。

- 第7个栏目表示：文件名。

这个东西，就是细工出慢活，一个一个不仅要知道是什么，还能讲出来，最重要的是还要专业，这样后面的才能接下去。






































