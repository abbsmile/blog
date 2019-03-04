---
title: df -h
date: 2017-03-04 21:25:50
categories:
- Linux
tags:
- Linux
---

`man df`看一下:
```
df -- display free disk space

-H  "Human-readable" output.  Use unit suffixes: Byte, Kilobyte, Megabyte, Gigabyte, Terabyte and Petabyte in order to reduce the number of digits to three or less using base 10 for sizes.
```
个人感觉很好理解了。

来一个感受一下：
```
 ~  df -h
Filesystem      Size   Used  Avail Capacity iused               ifree %iused  Mounted on
/dev/disk1s1   113Gi  102Gi  6.7Gi    94% 2351652 9223372036852424155    0%   /
devfs          201Ki  201Ki    0Bi   100%     696                   0  100%   /dev
/dev/disk1s4   113Gi  3.0Gi  6.7Gi    31%       3 9223372036854775804    0%   /private/var/vm
map -hosts       0Bi    0Bi    0Bi   100%       0                   0  100%   /net
map auto_home    0Bi    0Bi    0Bi   100%       0                   0  100%   /home
```

这是个常用命令，老大用得频率极高。啊，，，貌似运维上用的多，开发上也还好。以前总记不住，然后这边英文理解`display free disk space`,`Human-readable`可以帮助记忆。

总之，还是要学会看手册，看menu.