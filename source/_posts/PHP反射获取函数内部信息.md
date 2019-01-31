---
title: PHP反射获取函数内部信息
date: 2019-07-16 13:54:04
categories: 
- PHP
tags: 
- 反射
---

```
<?php

/**
 * 函数外部信息
 */
function Raw() {
    echo "函数内部信息!";
}

$ref_fun = new ReflectionFunction('Raw');

echo $ref_fun->getDocComment().PHP_EOL;
echo $ref_fun->getFileName().PHP_EOL;

echo $ref_fun->getStartLine().PHP_EOL;
echo $ref_fun->getEndLine().PHP_EOL;
?>

/**
 * 函数外部信息
 */
/Applications/MAMP/htdocs/test/a.php
6
8
```

通过反射类，可直接获取某个函数的内部信息，包括注释。

Reflection:
n.	反映; （关于某课题的） 思考; （声、光、热等的） 反射; 映像;

个人认为：思考，映像，更能显示出这个函数的功能。i
