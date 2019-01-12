---
title: distinct与paginate的冲突
date: 2019-01-12 10:24:33
categories:
- ThinkPHP
tags:
- PHP 
- ThinkCMF
- 分页
- SQL
---

在tp5中，用sql查询出来的数据，若有重复，用distinct不愧为一种简洁的方式。但，distinct与paginate是有冲突的。具体表现在:paginate会无视distinct的作用，按照原来搜索出的结果进行分页。

解决方法是：在paginate的第二个参数中传入总数。代码如下：

```
      $count  = $portalPostModel->alias('a')->field($field)
            ->join($join)
            ->join($join_event_hall)
            ->join($join_hall)
            ->join($join_center)
            ->where($where)
            ->distinct(true)
            ->order($condition)
            ->select();
        $articles        = $portalPostModel->alias('a')->field($field)
            ->join($join)
            ->join($join_event_hall)
            ->join($join_hall)
            ->join($join_center)
            ->where($where)
            ->distinct(true)
            ->order($condition)
            ->paginate(10, count($count));
```


