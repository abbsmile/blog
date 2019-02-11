---
title: 'sql:group by分组'
date: 2016-09-11 19:28:59
categories:
- SQL
tags:
- SQL
---

## 背景：
```
CREATE TABLE Student (
  SId   VARCHAR(10),
  Sname VARCHAR(10),
  Sage  DATETIME,
  Ssex  VARCHAR(10)
);
INSERT INTO Student VALUES ('01', '赵雷', '1990-01-01', '男');
INSERT INTO Student VALUES ('02', '钱电', '1990-12-21', '男');
INSERT INTO Student VALUES ('03', '孙风', '1990-05-20', '男');
INSERT INTO Student VALUES ('04', '李云', '1990-08-06', '男');
INSERT INTO Student VALUES ('05', '周梅', '1991-12-01', '女');
INSERT INTO Student VALUES ('06', '吴兰', '1992-03-01', '女');
INSERT INTO Student VALUES ('07', '郑竹', '1989-07-01', '女');
INSERT INTO Student VALUES ('09', '张三', '2017-12-20', '女');
INSERT INTO Student VALUES ('10', '李四', '2017-12-25', '女');
INSERT INTO Student VALUES ('11', '李四', '2017-12-30', '女');
INSERT INTO Student VALUES ('12', '赵六', '2017-01-01', '女');
INSERT INTO Student VALUES ('13', '孙七', '2018-01-01', '女');

CREATE TABLE Course (
  CId   VARCHAR(10),
  Cname NVARCHAR(10),
  TId   VARCHAR(10)
);
INSERT INTO Course VALUES ('01', '语文', '02');
INSERT INTO Course VALUES ('02', '数学', '01');
INSERT INTO Course VALUES ('03', '英语', '03');

CREATE TABLE Teacher (
  TId   VARCHAR(10),
  Tname VARCHAR(10)
);
INSERT INTO Teacher VALUES ('01', '张三');
INSERT INTO Teacher VALUES ('02', '李四');
INSERT INTO Teacher VALUES ('03', '王五');

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

## 过程

```
# 2. 查询平均成绩大于等于 60 分的同学的学生编号和学生姓名和平均成绩
SELECT
  S.SId,
  S.Sname
FROM Student AS S;

SELECT
  s.SId,
  s.Sname,
  t1.avgscore
FROM Student AS s
  INNER JOIN (
               SELECT
                 sc.SId,
                 AVG(sc.score) AS avgscore
               FROM sc
               GROUP BY sc.SId
               HAVING AVG(sc.score) >= 60
             ) AS t1
  ON s.SId = t1.SId
```

- 如果没有学生姓名Sname，其实不用管学生表Student;
- 查出来的结果也可作为一个，内联结联结的对象，可以当作一个表；
- group by与having在一起打团战；
- 笔者是在AVG函数这里遇到问题的，group by分组后，仍然可以在小组内应用AVG函数求平均值，这个也是厉害了。也是笔者记录的原因。

## 结论

having条件里，仍然可以用各种函数进而求值。