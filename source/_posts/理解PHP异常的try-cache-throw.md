---
title: 理解PHP异常的try-cache-throw
date: 2016-09-16 21:38:57
categories:
- PHP
tags:
- PHP
- 异常
---

## 聊两句

平时写代码，一者在框架的基础上扩充，二者前后左右都有同事写好的例子，跟着写就行了。所以，对一些最基本的知识，反而认识不到位。

像是空中楼阁，如果不触地，总有种不踏实感。

不过，换个角度，一开始如果学习那些基础，是学不下去的，很累。

金庸小说《笑傲江湖》中，令狐冲先学习独孤九剑，后来在种种际遇中学习各种内功，笔者认为是比较好的学习模式。如果像少林和尚一样先练十几年的马步，再学习其它的，非意志坚定者难成也。

而我们，大部分人，都是普通人。意志这东西，一点点自信都不该有。

扯远了……
 
## 关于异常

> 查看异常对象

```
$e = new Exception('抛出异常', 2);
print_r($e);
```

output:
```
Exception Object
(
    [message:protected] => 抛出异常
    [string:Exception:private] =>
    [code:protected] => 2
    [file:protected] => /Applications/MAMP/htdocs/test/Exception/01.php
    [line:protected] => 3
    [trace:Exception:private] => Array
        (
        )

    [previous:Exception:private] =>
)
```
虽然代码简单，但笔者从来没有这样去看看它到底是什么，长什么样……只是浮在半空中的感觉它很难。

或者，我们通过PHPStorm查看，原来它有那么多的方法：

![](http://pic.abble.top/15503267791250.jpg)

也可以用dash查看：
![](http://pic.abble.top/15503270616808.jpg)

对于异常，从一句话就可以扯出这么多。足以看出阅读源码的重要性了。

> try-cache-throw的关系

先来段代码：
```
$e = new Exception('抛出异常', 2);

try {
    throw $e;
} catch (Exception $e) {
    echo "接住".PHP_EOL;
}
```

try自然不用说了，throw相当于向天空中仍一个石子，对应的catch相当于接住这个石子。（当然接不接得住还得看后面的异常类是否是抛出的异常类了）

output:
```
 /Applications/MAMP/htdocs/test/Exception   master ●✚  php 01.php
接住
```

> 设置顶层异常处理类

```
class MyException extends Exception {

}

function my_exception_handler(MyException $e) {
   echo "good good good";
}
set_exception_handler('my_exception_handler');

class Test {
    public function __construct()
    {
        throw new YourException('这是一个自定义异常', 2);
    }
}

$t = new Test();
```

- 首先，知道它是干嘛的
Sets the default exception handler if an exception is not caught within a try/catch block. Execution will stop after the exception_handler is called.

- 函数中的参数不可少
Name of the function to be called when an uncaught exception occurs. This handler function needs to accept one parameter, which will be the exception object that was thrown.

当然，php7又不一样了，那是后面的事。








