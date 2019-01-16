---
title: select 1 in SQL
date: 2019-01-16 15:22:53
categories:
- SQL
tags:
- SQL
- MySQL
- ThinkPHP
- ThinkCMF
---

## 1. 背景

程序出了个bug，修改时要判断mysql某一行数据是否存在。因为这套程序是用原生sql写的，所以接触到了 select 1 这样的语句。

## 2. select 1 是什么？

首先，看下面3句话：

> 第一个：
```
select 1 from h_admin_menu;
```
返回结果是：
![image.png](https://upload-images.jianshu.io/upload_images/2875232-20b7c82f71798a51.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 第二个
```
# 注意下面的limit，这里只取一行，以提高效率
select 1 from h_admin_menu where id = 72 limit 1;
```
返回结果是：
![image.png](https://upload-images.jianshu.io/upload_images/2875232-ee347bb26cfb1c60.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 第三个
```
select 1 from h_admin_menu where id = 1772 limit 1;
```
返回结果是：
![image.png](https://upload-images.jianshu.io/upload_images/2875232-38140bf2b031779c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

注意无返回值。

从作用上来说，select 1, select *, select anycol长的差不多，功能也差不多，只是返回值不同。select 1的返回值永远是1，当然，如果有返回值的话。

效率方面：1>anycol>*  有时间可以验证，笔者在datagrip上观察执行时间，不过上面的执行时间不稳定，也是醉了。

下面来张图，自行体会，了解下：
![image.png](https://upload-images.jianshu.io/upload_images/2875232-475b272b7dcd8330.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 3. Db::query() 与 Db::execute() 的区别

-  第一种理解
query是查询，execute是执行，所以当select时用query，当增加、删除、修改时用execute

- 再进一步
query表示查询，返回的是表中搜索到的值；
execute表示执行，对表中的数据是有影响的，返回的是影响的行数；

- 所以：

> 场景1：

编辑保存时，如果内容未改变，仍调用update方法，返回值为0,但此时保存是成功的。
所以判断是否保存成功时，一般用：
```
if ($res !== false)
```

> 场景2 

当query：
```
select 1 from h_admin_menu where id = 72 limit 
```
返回值是数组那一套，如果恰巧无返回值，那么各种判断会让人跳楼的。

这个时候，便可以用execute了，，因为是受影响的行数，所以：结果只有1和0；很完美！


## 4. 好了，总结一下

判断某一行数据是否存在：
```
$sql = "select 1 from h_admin_menu where id = 72 limit ";
$isExist = Db::execute($sql);
```

结束！


















