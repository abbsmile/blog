---
title: ceil与floor
date: 2017-01-31 14:46:04
categories: 
- PHP
tags: 
- PHP 
- PHP函数
---

## 场景

在处理分页的时候，用到了这两个函数，也造成了一个不小的bug。特此记录下。

## ceil

查了下，有天花板的意思，向上取整。

## floor

自然，floor这个地板，也就是向下取整了。

## 说明

程序中开始用的是floor，然后当个数刚刚好时，总数/页数 恰巧为整数时，会出bug。

所以，当用到这两个函数时，要注意整数的情况。有时会出现一两个异类，造成临界情况出差错。

