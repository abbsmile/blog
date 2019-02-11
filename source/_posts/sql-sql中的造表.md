---
title: 'sql:sql中的造表'
date: 2016-08-21 19:33:44
categories:
- SQL
tags:
- SQL
---

## 背景：
```
CREATE TABLE SC (
  SId   VARCHAR(10),
  CId   VARCHAR(10),
  score DECIMAL(18, 1)
);
INSERT INTO SC VALUES ('01', '01', 80);
INSERT INTO SC VALUES ('01', '02', 90);
INSERT INTO SC VALUES ('01', '03', 99);
INSERT INTO SC VALUES ('02', '01', 70);
INSERT INTO SC VALUES ('02', '02', 60);
INSERT INTO SC VALUES ('02', '03', 80);
INSERT INTO SC VALUES ('03', '01', 80);
INSERT INTO SC VALUES ('03', '02', 80);
INSERT INTO SC VALUES ('03', '03', 80);
INSERT INTO SC VALUES ('04', '01', 50);
INSERT INTO SC VALUES ('04', '02', 30);
INSERT INTO SC VALUES ('04', '03', 20);
INSERT INTO SC VALUES ('05', '01', 76);
INSERT INTO SC VALUES ('05', '02', 87);
INSERT INTO SC VALUES ('06', '01', 31);
INSERT INTO SC VALUES ('06', '03', 34);
INSERT INTO SC VALUES ('07', '02', 89);
INSERT INTO SC VALUES ('07', '03', 98);
```

## 分析

> 1

```
# 1. 查询" 01 "课程比" 02 "课程成绩高的学生的信息及课程分数
SELECT *
FROM SC;

SELECT
  SId,
  score
FROM sc
WHERE sc.CId = '01'; # 所有语文课程

SELECT
  SId,
  score
FROM sc
WHERE sc.CId = '02'; # 所有数学课程

SELECT
  t1.SId,
  t1.score AS 语文,
  t2.score AS 数学
FROM
  (SELECT
     SId,
     score
   FROM sc
   WHERE sc.CId = '01') AS t1
  , (SELECT
       SId,
       score
     FROM sc
     WHERE sc.CId = '02') AS t2
WHERE
  t1.SId = t2.SId
  AND t1.score > t2.score;
```
成绩表很单一：学号，课程号，成绩。有一定冗余，但这样记录无疑是最好的。

- 首先，提取出01课程的学生和分数；提取出02课程的学生和分数；
- 想比较，两个条件：相同的学生，分数差异不同
```
t1.SId = t2.SId AND t1.score > t2.score;
```

记录这题目的意义在于：

from后面一般跟表名，这里面不是表名而是取出来的数据组合出来的表。

> 2

```
# 1.1 查询同时存在" 01 "课程和" 02 "课程的情况
SELECT *
FROM (SELECT
        SId,
        score
      FROM sc
      WHERE sc.CId = '01') AS t1, (SELECT
                                     SId,
                                     score
                                   FROM sc
                                   WHERE sc.CId = '02') AS t2
WHERE t1.SId = t2.SId;
```
这个同理。

> 3

```
# 1.2 查询'存在"01"课程' 但 '可能不存在"02"课程' 的情况(不存在时显示为 null )
SELECT
  t1.SId,
  t1.score AS 语文,
  t2.score AS 数学
FROM
  (SELECT
     SId,
     score
   FROM sc
   WHERE sc.CId = '01') AS t1
  LEFT JOIN (SELECT
               SId,
               score
             FROM sc
             WHERE sc.CId = '02') AS t2
    ON t1.SId = t2.SId;
```
这个主要是理解left join, inner join, right join；

> 4

```
# 1.3 查询不存在" 01 "课程但存在" 02 "课程的情况
SELECT SId
FROM SC
WHERE CId = '01'; # 1 ,2 ,3 ,4 ,5 ,6

SELECT SId
FROM SC
WHERE CId = '02'; # 1 ,2 ,3 ,4 ,5 ,7

SELECT *
FROM SC
WHERE SC.SId NOT IN (
  SELECT SId
  FROM SC
  WHERE CId = '01'
)
      AND SC.CId = '02';
```

分别画两个圈，两个圈的交集是既存在01课程也存在02课程的情况；非交集便可利用not in直接查询了。这里运用到了集合的思想。

## 总结

- from后面不仅仅可以跟表名，查询出来的也可以；
- sql语句的求解有时可以利用集合，但不全是；



