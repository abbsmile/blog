---
title: sql中的case 
date: 2016-11-22 20:24:20
categories:
- SQL
tags:
- SQL
---

## sql数据

[表数据可以在这里查到](http://www.abble.top/2016/11/17/%E7%9B%B8%E5%85%B3%E5%AD%90%E6%9F%A5%E8%AF%A2%E5%92%8C%E4%B8%8D%E7%9B%B8%E5%85%B3%E5%AD%90%E6%9F%A5%E8%AF%A2/)

## 记录主要是为了case when

> 题目

查询各科成绩最高分、最低分和平均分;

以如下形式显示：课程ID，课程name，最高分，最低分，平均分，及格率，中等率，优良率，优秀率,
及格为>=60，中等为：70-80，优良为：80-90，优秀为：>=90

要求输出课程号和选修人数，查询结果按人数降序排列，若人数相同，按课程号升序排列

> sql

```
SELECT
  SC.CId,
  Course.Cname,
  max(sc.score)              AS 最高分,
  min(sc.score)              AS 最低分,
  AVG(sc.score)              AS 平均分,
  count(*)                   AS 选修人数,
  sum(CASE WHEN SC.score >= 60 THEN 1 ELSE 0 END) / count(*) AS 及格率,
  sum(CASE WHEN SC.score >= 70 AND SC.score <80 THEN 1 ELSE 0 END) / count(*) AS 中等率,
  sum(CASE WHEN SC.score >= 80 AND SC.score <90 THEN 1 ELSE 0 END) / count(*) AS 优良率,
  sum(CASE WHEN SC.score >= 90 THEN 1 ELSE 0 END) / count(*) AS 优秀率
FROM SC ,Course
  WHERE SC.CId = Course.CId
GROUP BY SC.CId
ORDER BY count(*) DESC, SC.CId ASC;
```

- count(*)在group by里面同样可以统计小组人数;
- A/B 的形式可以这样使用；
- `CASE WHEN SC.score >= 90 THEN 1 ELSE 0 END`是一个新的认识；因为代码中使用原生sql极少，使用这样的sql语句极少，虽然见过这样的sql,但没有亲自学习过。