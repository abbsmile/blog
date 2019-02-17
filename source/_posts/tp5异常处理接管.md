---
title: tp5异常处理接管
date: 2017-08-17 15:26:40
categories:
- ThinkPHP
tags:
- ThinkPHP
---

## 为什么要考虑这块知识

这几年，特别是移动端兴起后，项目大多是前后端分离的。前后端分离带来的便是写接口。而，错误异常处理，在接口处理中，显得尤为重要。i

项目想要优雅，在开始搭建时，就应该把异常处理模块封装好。从OOP的角度来看，完美实现了"封装"的特点；从AOP的角度来看，也是有那么点味道的。

如果封装的好，到了其它的项目，有些东西也可以直接拷过去。

## tp5中的异常处理接管

> 1. 新建`think\exception\Handl`的子类`ExceptionHandle`，重写render()方法

```
class ExceptionHandler extends Handle
{
    private $code;
    private $msg;
    private $data;

    public function render(Exception $e)
    {
        if ($e instanceof BaseException) {
            $this->code = $e->code;
            $this->msg = $e->msg;
            $this->data = $e->data;
        } else {
            $this->code = '500';
            $this->msg = '服务器内部错误';
            $this->data = '';
        }

        $result = ['code' => $this->code, 'msg' => $this->msg, 'data' => $this->data,];
        return json($result);
    }
}
```


> 2.在tp5的配置文件中引入新建的类，这里是`ExceptionHandle`

config/app.php文件里：
```
// 异常处理handle类 留空使用 \think\exception\Handle
'exception_handle'       => '\\app\\lib\\exception\\ExceptionHandler',
```

## 自定义异常类的解析

访问接口，对后端开发者来说，异常可以分为两种。
- 用户访问接口时，参数不规范或者当前服务器没有此类资源（这不是接口本身的错误，应该如何访问要返回给客户端）
- 内部服务器错误(接口本身自己的错误，不用返回错误给客户端，服务器人员知道就行)

第一种异常，便是需要我们自己封装的异常。`class ExceptionHandler extends Handle`有关于此类代码的引用：
```
 if ($e instanceof BaseException) {
            $this->code = $e->code;
            $this->msg = $e->msg;
            $this->data = $e->data;
        } else {
            $this->code = '500';
            $this->msg = '服务器内部错误';
            $this->data = '';
        }
```
对，就是`BaseException`。

所以搭好架构后，我们只需要根据BaseException引申出一系列自定义异常类。等在业务中，即时抛出此类异常对象，这些没有被cache的异常，全部交由ExceptionHandler处理。

如此，接口中异常部分，便有了个雏形！




