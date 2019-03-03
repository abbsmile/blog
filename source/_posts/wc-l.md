---
title: wc -l
date: 2017-03-03 20:06:31
categories:
- Shell
tags:
- Shell
- Linux
---

## 来一个shell

```
[ `who | wc -l` -le 1 ] && echo "yes"
```

## who

笔者常用的`whoami`,这个当然更全面一点。`man who`可以看见全部信息。

## wc

`wc`以前遇到过，不过今天刚接触时还是失忆了。`man wc`后`-l`很好，这个在程序的应用场景中应该会很多。个人感觉`wc`比上面的`who`重要多了。

## -le的扩展

来个总结：
```
-ne  ：  （not equal） 不相等

-gt   ：    (greater than) 大于

-lt    ： (less than) 小于

-ge  ：    (greater than or equal) 大于或等于

-le   ：    (less than or equal)小于或等于
```

哈，笔者复制的，这个笔者以前研究过。不过今天看见后两个,`-ge``-le`时还是有点陌生。不仅在shell，PHP前后端不分离的项目中，渲染前端模板判断时，也常会用到这些判断。

以前搞wordpress时，老大也提到过，那是第一次接触这东西。

还有一个要熟知,上面的这些个在shell中叫做：
- 关系运算符
关系运算符只支持数字，不支持字符串，除非字符串的值是数字。

在Shell中，字符串自有字符串运算符。这些概念性东西，在这里显得尤为重要了。