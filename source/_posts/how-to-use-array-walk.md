---
title: how to use array_walk()
date: 2019-01-11 14:06:48
categories:
- PHP
tags:
- PHP
- 数组
- 函数
---

这边放两个小例子，然后说明下 `array_walk()`的用法。以后有机会，再把类似的几个函数放一起，谈谈效率。

1.
```
function myfunction($value,$key)
{
	echo "The key $key has the value $value".PHP_EOL;
}

$a = array("a"=>"red","b"=>"green","c"=>"blue");
array_walk($a,"myfunction");
```

2.
```
$a = array("a"=>"red","b"=>"green","c"=>"blue");
array_walk($a, function($value, $key) {
	echo "The key $key has the value $value".PHP_EOL;
});
```

ok，上面两函数的结果是一样的，只不过一个用的函数，一个用的闭包。
首先：了解有这样一种写法；
其次：注意下函数中参数的顺序，对，就是这样，第一个是`$value`,第二个是`$key`

然后，我们看下面的例子：

3.
 
```
function example(&$value)
{
    $value = $value + 5;
}

$arrLearnIds = [1, 2, 3];
array_walk($arrLearnIds, 'example');

var_dump($arrLearnIds);
```


4.

```
$arrLearnIds = [1, 2, 3];
array_walk($arrLearnIds, function (&$value) {
    $value = $value + 5;
});

var_dump($arrLearnIds);
```

这里还是要强调一下取地址符&。因为是取地址符，所以改变的是数组，这一点要清楚。

然后再看一眼这里的闭包，会感觉代码很优美。。。！！！

