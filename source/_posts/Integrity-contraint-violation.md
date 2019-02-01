---
title: Integrity contraint violation
date: 2017-11-18 19:50:29
categories: 
- MySQL
tags:
- PHP MySQL
---

刚刚写简书无意识回到首页时，看见一个关于学习方法的醒目的标题……感觉自己最近心态变了。以前看见这些至少会点开看一下，现在，像看见传销一样。我不否认学习方法的重要性，只是，更倾向于马克思辩证法了。

又想起修身，齐家，治国，平天下，这个次序确实很有味道。

怪不得曾国藩反而应用文写得好。确实，经历多了，小清新、文艺那一套，反而不如实实在在的说明文应用文。题外话了……

__操作数据库的时候，总是会碰上以下图片所示的问题。那几个单词背了无数遍，看起来还是陌生。所以想着，借此机会，一个单词一个单词的过，一个bug一个bug的分析。__

![秦时明月汉时关，万里长征人未还。](http://upload-images.jianshu.io/upload_images/2875232-22f9fe5116ac5390.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)

![但使龙城飞将在，不教胡马度阴山。](http://upload-images.jianshu.io/upload_images/2875232-262539cc2c7e7284.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)

- 首先，PDOException是什么？
  这个在以后的简书中会单独分析。

- SQLSTATE[23000]
  23000状态码：代码插入数据时主键重复。

我们来看一下这几个单词：`Integrity constraint violation`
integrity: 一方面指人的品格方面完整、正直等；另一方面指实物方面完整。
1、If you have integrity, you are honest and firm in your moral principles.
2、The integrity of something such as a group of people or a text is its state of being a united whole.

constraint: 约束。
a device that retards[阻碍] something's motion。
constraint是个很有意思的词。总体而言，一个发力方，一个受力方和一个第三者之间的关系。有意思的是这个第三者，有时和发力方有关系，有时和受力方有关系，有时和两者都没关系。这个有兴趣可以写篇议论文了。
在数据库这个例子当中，好比我想杀人，但是对方是总统。对方的保护系统是约束。重要的是：这个约束和我没有关系，只和对方有关系。
扯远了……

violation:违背，违反。
entry to another's property without right or permission。

合在一起，违反了完整性约束。就是有一套完整的规则，我们违背了它。类似在社会主义国家办妓院一样。这个国家的法律可称之为一个完整性规则。而开妓院这个行为，违背了它，当然不行。但是澳洲就不一样，，对于数据库，同样如此。

刚刚百度了一下，完整性规则分为以下几种： 
domain Integrity constrains:包括检查（CHECK）、[默认值]（DEFAULT）、不为空（NOT NULL）、外键（FOREIGN KEY）等约束。
Entity integrity: 主键值不能重复
Referential Integrity：主键外键那一套
user defined integrity：自己创建的的那一套

这个也可以写一篇简书了，暂时打住。我们今天上面的问题属于user definde integrity.

- ON DELETE CASCADE ON UPDATE CASCADE

我们还是先看单词：cascade [kæˈsked] 
级联，有种串联的意思。雨啊……水啊……

![英英解释还是看不懂，倒是这个串联，来自物理上的形象词更适合我](http://upload-images.jianshu.io/upload_images/2875232-857b4e51f05e364b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

现在我们可以谈到数据库了：
- 数据库定义外键时，当主键表中的被参考列数据发生变化时，外键应该如何去做？有下面四种方式。
 NO ACTION | SET NULL | SET DEFAULT | CASCADE
前面三个好理解，毕竟单词简单，最后一个可以说是同上。你更新，我便更新；你删除，我便随你而去。

- 下面我们来看一下：cmf_teacher_course_ibfk_2是如何定义的

```
| cmf_teacher_course | CREATE TABLE `cmf_teacher_course` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `teacher_uid` bigint(20) unsigned NOT NULL,
  `course_id` bigint(20) unsigned NOT NULL,
  `price` decimal(8,2) DEFAULT '0.00' COMMENT '课程价格',
  `create_time` int(11) NOT NULL DEFAULT '0' COMMENT '创建时间',
  `create_uid` bigint(20) NOT NULL DEFAULT '0' COMMENT '创建用户',
  `status` tinyint(1) DEFAULT '1' COMMENT '状态，1:正常,0:禁用',
  `remark` varchar(255) DEFAULT NULL COMMENT '备注',
  PRIMARY KEY (`id`),
  UNIQUE KEY `idx_u_teacher_course` (`teacher_uid`,`course_id`),
  KEY `fk_course` (`course_id`),
  CONSTRAINT `cmf_teacher_course_ibfk_1` FOREIGN KEY (`course_id`) REFERENCES `cmf_courses` (`id`) ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT `cmf_teacher_course_ibfk_2` FOREIGN KEY (`teacher_uid`) REFERENCES `cmf_user` (`id`) ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COMMENT='教师课程表' 
```
好了，利用 show create table cmf_teacher_course看到这里，我们便很清晰：
数据库education
表cmf_teacher_course
里面的约束cmf_teacher_course_ibfk_2不成立。

同时，通过前面的讨论，对
a foreign key constraint fails括号里面的错误也学会了断句。

总结起来，认识单词并根据数据库的基本知识断句很重要。（sql state = 23000）




















