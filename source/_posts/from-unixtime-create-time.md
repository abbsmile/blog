---
title: from_unixtime(create_time)
date: 2018-02-02 22:32:50
- SQL
tags:
- SQL
---

查看数据库数据，如果时间`比如create_time`是unix时间戳，必然很不方便。

可以使用from_unixtime函数进行格式转换。效果如下：
```
MariaDB [education]> select id, from_unixtime(create_time)
 from cmf_student_calendar where id = 138;
+-----+----------------------------+
| id  | from_unixtime(create_time) |
+-----+----------------------------+
| 138 | 2018-02-02 20:31:18        |
+-----+----------------------------+
1 row in set (0.00 sec)


MariaDB [education]>  select id, from_unixtime(1517574678, '%Y-%m-%d')
 from cmf_student_calendar where id = 138; 
| id  | from_unixtime(1517574678, '%Y-%m-%d') |
+-----+---------------------------------------+
| 138 | 2018-02-02                            |
+-----+---------------------------------------+
1 row in set (0.00 sec)
````

- from_unixtime 有两个参数
  - 第一个参数可以是数据库字段，也可以是unix时间戳。
  - 第二个参数用于定义格式。可缺省。具体格式百度百科。


