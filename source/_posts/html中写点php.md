---
title: html中写点php
date: 2019-01-12 11:24:39
categories:
- HTML
tags:
- PHP
- HTML
---

php将数据渲染到html中时，对数据有两种处理方式。大多数是直接在后台进行处理；但，直接在html中处理数据有时也能带来方便。

这样，需求来了：如何在html中嵌入php代码？直接上代码：

```
<td>
  <?php 
      echo date('Y-m-d H:i',strtotime($vo['create_datetime']))
  ?>
</td>
```
下面的代码虽然不怎么优雅，但对理解这个知识应该更好:

```
<?php
  $time = $vo['update_datetime'];
  $time = substr($time, 0, strlen($time)-3);
  echo "<td>".$time."</td>";
?>
```
结束！
