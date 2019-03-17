---
title: TP5中where里面闭包写法引起的思考
date: 2018-01-13 22:52:56
categories:
- ThinkPHP
tags:
- ThinkPHP
---

知其然已经很难了，为什么要知其所以然？王阳明的知行合一，或不仅仅为了知行合一而知行合一。做什么，都是为现实服务的。行，为了更好的知，而知，为了更好的行。最终目的，当然每个人不一样，但一定有。

知其所以然，当然是更好的知其然。这样，不管困难再怎么排列组合，也能得心应手。万变不离其宗，同样的道理。

> 看一段TP5上面的代码：
```
 $data = DB::name('company')->select();
 $data = DB::table('company');
```
每个人都有自己的习惯，有的喜欢用Db::name，有的喜欢用DB::table。也有人，只知道DB::name；当然也有人只知道Db::table。

不要感觉不可思议，我曾是里面的一员，至今记得那个时候看到Db::table时眼睛一亮：还有这样的？

然后，然后记住了，然后就没了……（和别人的差距就在这里）

又过了好久，想看一下两个有什么不同，于是看了一下declaration，一个鼠标点击的事，一秒钟的事。有点感觉了。

![image.png](http://upload-images.jianshu.io/upload_images/2875232-1f14885d7ab0d0dc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)

> 查询器query对象

于是，那时候了解了查询器query对象。

```
* @method Query name(string $name) static 指定数据表（不含前缀）
* @method Query where(mixed $field, string $op = null, mixed $condition = null)
 ```
通过比较这俩哥们返回值，对链式查询有了感觉。

```
 * @method mixed find(mixed $data = null) static 查询单个记录
```
再把这哥们加上去，明白了他们不是同一个山寨的。不过是搭伙过日子。这个时候，再去理解在where里面加上闭包，很舒服，很自然。

> where里面加上个闭包

```
$data  = Db::table('banner_item')
            ->where(function ($query) {
                $query->where('id', 'eq', $id);
            })
            ->select();
```

where里面，是一个匿名函数。函数很熟悉，匿名函数不过是少了个函数名称。

然后呢？传过来一个参数，这个参数便是query对象了。有了query对象，函数里面的写法便和上面一样了，想怎么写就怎么写了。我们也知道为什么里面不能链上find()或select()了。

最后，便是条件里面如何传进去参数，加上use ($id)

```
$data  = Db::table('banner_item')
            ->where(function ($query) use ($id){
                $query->where('id', 'eq', $id);
            })
            ->select();
```

如果再加上我们知道，where有三种写法：表达式法，数组法，然后闭包法。这样，对理解便更深刻了。

会写代码是一种技巧，但是透过现象看本质，学其它东西时，会更好的接受。或者提升一个档次，这种思维很最重要。































