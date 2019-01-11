---
title: centOS上汉字乱码
date: 2019-01-11 14:48:06
categories:
- CentOS
tags:
---

ssh刚进入centOS时，出现这么一行：
```
Centos warning: setlocale: LC_CTYPE: cannot change locale (UTF-8): No such file or directory
```
然后查看代码，代码中的中文字符全部为乱码。

笔者以前遇到过这样的问题，解决的比较麻烦，下面这个亲试不错：
[cannot change locale (UTF-8)](https://gist.github.com/mes01/c8634bd4f94f21e4f4259e257509d68f)

建立文件：
```
vi /etc/environment
```

添加内容：
```
LANG=en_US.utf-8
LC_ALL=en_US.utf-8
```


