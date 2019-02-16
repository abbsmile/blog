---
title: __toString方法
date: 2016-09-01 21:53:12
categories:
- PHP
tags:
- PHP
---

## 先来看文档

The __toString() method allows a class to decide how it will react when it is treated like a string. 

For example, what echo $obj; will print. This method must return a string, as otherwise a fatal E_RECOVERABLE_ERROR level error is emitted.

注：
emit:发出，发射

Warning
You cannot throw an exception from within a __toString() method. Doing so will result in a fatal error.

```
<?php
// Declare a simple class
class TestClass
{
    public $foo;

    public function __construct($foo)
    {
        $this->foo = $foo;
    }

    public function __toString()
    {
        return $this->foo;
    }
}

$class = new TestClass('Hello');
echo $class;
?>
```

## 简单小结一下

- "对象引用"被当成字符串时，会调用__toSting方法；
- PHP中凡是以`__`开头的方法，会在某个时间点被调用。这个和iOS中的某些方法差不多；
- `__toString`方法中不能抛出异常。
