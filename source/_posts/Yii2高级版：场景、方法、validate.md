---
title: Yii2高级版：场景、方法、validate
date: 2018-08-19 20:43:17
categories:
- Yii2
tags:
- Yii2
- PHP
---

## 概述

我们从框架的角度，想像一个http请求的全过程。

- 请求过来，首先要判断请求类型：get/post/put/delete
- 设置验证场景
- 装载数据并验证
- 具体的业务逻辑
- 返回请求的数据或抛出异常

下面就当前项目，描述一种搭配方案。异常部分总结放在以后。

## 判断请求类型

> 了解两个类

- `Class yii\rest\Controller`

Controller is the base class for RESTful API controller classes.

继承以实现接口的封装；

- `Class yii\filters\VerbFilte`

VerbFilter is an action filter that filters by HTTP request methods.

It allows to define allowed HTTP request methods for each action and will throw an HTTP 405 error when the method is not allowed.

To use VerbFilter, declare it in the behaviors() method of your controller class. For example, the following declarations will define a typical set of allowed request methods for REST CRUD actions.

```
public function behaviors()
{
    return [
        'verbs' => [
            'class' => \yii\filters\VerbFilter::className(),
            'actions' => [
                'index'  => ['GET'],
                'view'   => ['GET'],
                'create' => ['GET', 'POST'],
                'update' => ['GET', 'PUT', 'POST'],
                'delete' => ['POST', 'DELETE'],
            ],
        ],
    ];
}
```

文档上讲得很清楚，这里权当搬运工了。我们再查看`Class yii\rest\Controller`

```
behaviors() public method
{@inheritdoc}
public void behaviors ()
```

所以，完全可以继承，以实现对`http request methods`的甄别。

> `Class yii\rest\Controller`下面的这句话，感觉有必要复制一下：

```
Controller implements the following steps in a RESTful API request handling cycle:

Resolving response format (see yii\filters\ContentNegotiator);
Validating request method (see verbs()).
Authenticating user (see yii\filters\auth\AuthInterface);
Rate limiting (see yii\filters\RateLimiter);
Formatting response data (see serializeData()).
For more details and usage information on Controller, see the guide article on rest controllers.
```
其中有一个`Validating request method`,这也是能找到`Class yii\filters\VerbFilte`的原因，总有内在逻辑关系的。

## 设置验证场景

这里没有其它的，就想把里面的代码一行一行分析一遍。




