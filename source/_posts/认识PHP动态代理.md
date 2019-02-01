---
title: 认识PHP动态代理
date: 2016-08-01 23:44:22
categories:
- PHP
tags:
- 代理
- PHP
- 反射
---

```
<?php

class child
{
    public function eat()
    {
        echo "child eat!";
    }
}

class Nanny
{
    private $obj;

    function addObj($obj)
    {
        $this->obj[] = $obj;
    }

    function __call($name, $arguments)
    {
        foreach ($this->obj as $obj) {
            $ref_obj = new ReflectionClass($obj);
            if ($ref_obj->hasMethod($name)) {
                $ref_method = $ref_obj->getMethod($name);
                if ($ref_method->isPublic() && !$ref_method->isAbstract()) {
                    if ($ref_method->isStatic()) {
                        $ref_method->invoke(null);
                    } else {
                        $ref_method->invoke($obj);
                    }
                }
            }
        }
    }
}

$nanny_obj = new Nanny();
$nanny_obj->addObj(new child());
$nanny_obj->eat();
```

如上所示，两个类并无直接联系，但利用反射巧妙形成了一个动态代理。
