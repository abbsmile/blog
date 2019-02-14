---
title: High Sierra+XAMPP+ terminal下打开mysql
date: 2018-01-07 23:38:43
categories:
- MySQL
tags:
- MySQL
---

环境：macOS High Sierra系统 + XAMPP7.0.2-1
问题：termial命令行下，$mysql
`Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)`


过程：百度下试了几种方法，看上去不错，结果有点尴尬。最后在StackOver上面找到了一个好的方法。
[stackoverflow上面别人的第一个回答](https://stackoverflow.com/questions/19749783/tried-every-thing-still-getting-error-2002-hy000-cant-connect-to-local-mysql)

看别人的问题，然后再看解决方法，整个流程读下来很有意思。简而言之，核心就是创建一个软连接(ps:开始我好像也是用的这个方法，失败了;后来到了stackoverflow这里可以了，这个要看调试的具体情况了)：
`ln -s /applications/xampp/xamppfiles/var/mysql/mysql.sock /tmp/mysql.sock`

## 这样直接进去 
```
/Applications/xampp/xamppfiles/bin/mysql -u root -p
```
