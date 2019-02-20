---
title: group by只是一个附加条件
date: 2016-11-20 22:12:20
categories:
- SQL
tags:
- SQL
---

## sql数据

[表数据可以在这里查到](http://www.abble.top/2016/11/17/%E7%9B%B8%E5%85%B3%E5%AD%90%E6%9F%A5%E8%AF%A2%E5%92%8C%E4%B8%8D%E7%9B%B8%E5%85%B3%E5%AD%90%E6%9F%A5%E8%AF%A2/)

## 对`group by`的理解

> group by只是一个附加条件

```
SELECT *
FROM SC
WHERE score < 60
GROUP BY SId HAVING count(*) >=2;
```

如果把最后一句去掉，变成下面这样，
```
SELECT *
FROM SC
WHERE score < 60;
```
sql语句同样可以运行。只是加上`group by`后，等于在原来的基础上，又顺序运行了一条语句。

> having 里面也可以用聚合函数

```
GROUP BY SId HAVING count(*) >=2;
```

## 题目与误区

> 题目

查询两门及其以上不及格课程的同学的学号，姓名及其平均成绩

```
SELECT Student.SId, Student.Sname, AVG(SC.score)
FROM SC, Student
WHERE Student.SId = SC.SId
      And score < 60
GROUP BY SId HAVING count(*) >=2
```

> 笔者的误区

- 如果同一个学生有两个或三个学生，则score只会取查到的第一个


```
SELECT Student.SId, Student.Sname, SC.score
FROM SC, Student
WHERE Student.SId = SC.SId And SC.score < 60
GROUP BY Student.SId;
```
```
04,李云,50.0
06,吴兰,31.0
```

- 未分组，`AVG`会取全部学生的平均分数

```
SELECT Student.SId, Student.Sname, SC.score, AVG(SC.score)
FROM Student, SC
WHERE Student.SId = SC.SId;
```
```
01,赵雷,80.0,68.55556
```

- `group by`与`avg`一起，avg则取每组的平均成绩
