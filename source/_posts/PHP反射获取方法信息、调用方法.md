---
title: PHP反射获取方法信息、调用方法
date: 2016-07-21 19:30:10
categories: 
- PHP
tags:
- PHP
- 反射
---

直接上代码：
```
<?php

class Shell {
    function A() {
        echo "无参数public方法";
    }

    function A1($str) {
        echo "有参数public方法".$str;
    }

    private function B() {
        echo "私有方法".PHP_EOL;
    }

    static function C() {
        echo "我是静态方法".PHP_EOL;
    }
}

$a = new Shell();
//$ref_obj = new ReflectionClass('Shell');
$ref_obj = new ReflectionClass($a); // 都可以

echo "1. 所有的方法：".PHP_EOL;
$arr_obj_methods = $ref_obj->getMethods();
var_dump($arr_obj_methods);

echo "2. 判断是否有A方法：".PHP_EOL;
$has_A = $ref_obj->hasMethod('A');
echo $has_A;
echo "<br/>";

echo "3. 判断A是否是公共方法：".PHP_EOL;
$rel_method = $ref_obj->getMethod('A');
var_dump($rel_method->isPublic());

echo "4. 判断A是否是私有方法：".PHP_EOL;
$rel_method = $ref_obj->getMethod('B');
var_dump($rel_method->isPrivate());

echo "5. 判断A是否是静态方法".PHP_EOL;
$rel_method = $ref_obj->getMethod('C');
var_dump($rel_method->isStatic());

echo "6. 调用静态方法:";
echo "<br/>";
$rel_method = $ref_obj->getMethod('C');
if ($rel_method->isPublic() && !$rel_method->isAbstract()) {
    if ($rel_method->isStatic()) {
        $rel_method->invoke(null);
        echo "<br/>";
    }
}

echo "7. 调用动态方法:";
echo "<br/>";
$rel_method = $ref_obj->getMethod('A');
if ($rel_method->isPublic() && !$rel_method->isAbstract()) {
    if ($rel_method->isPublic()) {
        $rel_method->invoke($a);
        echo "<br/>";
    }
}

echo "8. 调用有参数动态方法:";
echo "<br/>";
$rel_method = $ref_obj->getMethod('A1');
if ($rel_method->isPublic() && !$rel_method->isAbstract()) {
    if ($rel_method->isPublic()) {
        $rel_method->invoke($a, '(这是参数)');
        echo "<br/>";
    }
}
```

利用反射类操作方法，注意两点：
1. 调用时注意一个抽象类要排除
2. 调用静态方法和调用公共方法不同。不过这个也方便排除错误，主要是前一个错误有点尴尬。
3. PHP_EOL貌似不行，或许只有在命令行中才起作用。
