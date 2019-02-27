---
title: PHP-BCMath
date: 2018-02-27 22:23:54
categories:
- PHP
tags:
- PHP函数
---

## 问题

```
$a = 0.7;
$b = 0.1;
$c = 0.8;

if ($a + $b == $c) {
    echo "相等".PHP_EOL;
} else {
    echo "不相等".PHP_EOL;
}
```

output:
```
不相等
```

## 解决问题

> 1.Introduction

For arbitrary precision mathematics PHP offers the Binary Calculator which supports numbers of any size and precision up to 2147483647 (or 0x7FFFFFFF) decimals, if there is sufficient memory, represented as strings.

arbitrary: 乱; 随意的，任性的，随心所欲的; 主观的，武断的; 霸道的，专制的，专横的
decimals：小数( decimal的名词复数 )

represented as strings:用字符串表示的.这个翻译时提到前面去,最前面。

> 2.BC Math Functions

这个其实在dash中查找极为方便，这里随意复制下吧！重点是要知道有BC Math Functions这个东西，然后用到的时候能快速找到！手册是比google更方便的东西！

bcadd — Add two arbitrary precision numbers
bccomp — Compare two arbitrary precision numbers
bcdiv — Divide two arbitrary precision numbers
bcmod — Get modulus of an arbitrary precision number
bcmul — Multiply two arbitrary precision numbers
bcpow — Raise an arbitrary precision number to another
bcpowmod — Raise an arbitrary precision number to another, reduced by a specified modulus
bcscale — Set default scale parameter for all bc math functions
bcsqrt — Get the square root of an arbitrary precision number
bcsub — Subtract one arbitrary precision number from another

> 3.BC是什么意思？代表什么？

刚好网上看见这句话，抄下来了：

 BCMath扩展提供了一套bc（Binary Calculator）数学函数，它是一个高精度运算的函数库，可以准确地对任意精度的数字进行运算。