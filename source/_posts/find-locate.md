---
title: find && locate
date: 2018-01-07 22:44:04
categories:
- Linux
tags:
- Linux
---

- find
`find . -name "AdminUser*" -ls | grep "AdminUser"`
这条命令很有用

- locate
`locate /etc/sh`
这是网上的经典例子，要注意一点，是从根目录开始的，要绝对路径。相对路径是不行的。
