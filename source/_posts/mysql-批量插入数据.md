---
title: 'mysql:批量插入数据'
date: 2019-01-11 15:48:23
tags:
---

同事要测一个需求，叫我向数据库中批量插入一些数据。之前没做过这个,所以不敢懈怠, 最后发现挺好玩的，也把存储过程实际应用了一把。

不多说，直接上代码：
```
CREATE PROCEDURE unknown()
  BEGIN
    DECLARE num INT;
    SET num = 13000;
    WHILE num < 13500 DO
      set names latin1;
      INSERT INTO learn_questions (FCorpUin, FQuestion, FTimes, FSyncId, FCreateTime, FSyncTime, FIdlist, FRobotId)
        VALUE
        (2852199100, 'test', 2, num, 1536629393, 1536629393, "", 7777777777);
      SET num = num + 1;
    END WHILE;
  END;
```

运行之后，调用是这个：
```
CALL unknown();
```

插入之后，记得删除：
```
DROP PROCEDURE IF EXISTS unknown;
```

其它语法，笔者找时间总结一个，这是个缺口。

