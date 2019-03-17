---
title: php中两种添加数组元素的小技巧
date: 2018-02-27 22:39:56
categories:
- PHP
tags:
- PHP
---

```
I've done a small comparison between array_push() and the $array[] method and the $array[] seems to be a lot faster.

<?php
$array = array();
for ($x = 1; $x <= 100000; $x++)
{
    $array[] = $x;
}
?>
takes 0.0622200965881 seconds

and

<?php
$array = array();
for ($x = 1; $x <= 100000; $x++)
{
    array_push($array, $x);
}
?>
takes 1.63195490837 seconds

so if your not making use of the return value of array_push() its better to use the $array[] way.

Hope this helps someone.
```

没验证过上面的正确性，只是偶然看见$array[] 方法，感觉比较新鲜，查了一下。

1. 知道了原来添加数组原素还有这样一种方法;
2.  [array_push](http://php.net/manual/en/function.array-push.php) php.net网站上的评论还是很不错的，这方面给我打开了一扇新的窗户。上面文章是对链接中的部分评论。
