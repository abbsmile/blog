---
title: mysql commands
date: 2017-11-08 23:39:45
categories:
- MySQL
tags:
- MySQL
- command
---

mysql-The world's most popular open source database   

  ```
List of all MySQL commands:
Note that all text commands must be first on line and end with ';'
?         (\?) Synonym for `help'.
clear     (\c) Clear the current input statement.
connect   (\r) Reconnect to the server. Optional arguments are db and host.
delimiter (\d) Set statement delimiter.
edit      (\e) Edit command with $EDITOR.
ego       (\G) Send command to mysql server, display result vertically.
exit      (\q) Exit mysql. Same as quit.
go        (\g) Send command to mysql server.
help      (\h) Display this help.
nopager   (\n) Disable pager, print to stdout.
notee     (\t) Don't write into outfile.
pager     (\P) Set PAGER [to_pager]. Print the query results via PAGER.
print     (\p) Print current command.
prompt    (\R) Change your mysql prompt.
quit      (\q) Quit mysql.
rehash    (\#) Rebuild completion hash.
source    (\.) Execute an SQL script file. Takes a file name as an argument.
status    (\s) Get status information from the server.
system    (\!) Execute a system shell command.
tee       (\T) Set outfile [to_outfile]. Append everything into given outfile.
use       (\u) Use another database. Takes database name as argument.
charset   (\C) Switch to another charset. Might be needed for processing binlog with multi-byte charsets.
warnings  (\W) Show warnings after every statement.
nowarning (\w) Don't show warnings after every statement.
```
本来准备一个一个学的，然后发现不切实际。命令行里的这套东西在于查，而不在于学。主要用于复习，牢记，查询的场合。 

  `\?`很重要，不容置疑。

![\c 用于清除前面写的sql ](http://upload-images.jianshu.io/upload_images/2875232-149d24de7c0b8c84.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![\q用于离开mysql](http://upload-images.jianshu.io/upload_images/2875232-d38dd80e3c87f466.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![\u用于切换数据库](http://upload-images.jianshu.io/upload_images/2875232-5349b92b6347b23e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)

![\\!用于执行shell命令](http://upload-images.jianshu.io/upload_images/2875232-a2d5e7755505f9d1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 命令行上写sql语句的几个小技巧
- ctrl+a 将光标移到最前面
- ctrl+e 将光标移到最后面

> \G

这是隔了很长时间后，后面补充的。`\G`这个命令最近用的比较多。查询数据的时候在后面加个`\G`,可以让数据纵向展示，更方便测试。

以前比较反感在命令行中直接操作数据。明明有那么多优秀的ide，何必呢？现在，可能用的时间长了，安装的那些优秀ide反而成了摆设。时间这东西，总会让人搬起石头砸起自己的脚。






