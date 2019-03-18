---
title: Getting Checkbox Values in jQuery
date: 2018-03-13 23:59:29
categories:
- HTML
tags:
- HTML
---

- 本篇文章最重要的不是下面的链接，不是方法的细节，而是这个标题
`Getting Checkbox Values in jQuery`。 锻炼英文思维，知道如何用英文搜索。

- 这个链接上面的解释不错，讲的很仔细
[Getting Checkbox Values in jQuery](https://phppot.com/php/getting-checkbox-values-in-jquery/)

- 如果懒得看链接，可以看下面：
```
<input type="checkbox" class="js-check" data-yid="js-check-y" 
data-xid="js-check-x" 
name="ids[]" 
value="{$vo.id}" 
data-name="{$vo.name}                
```
```
 <button id="btnSubmit" type="button" class="btn btn-info btn-sm">添加</button>
```
```
    $(document).ready(function () {
        $("#btnSubmit").click(function () {
            // 2.1 选中属性组id
            var selectedAttrGroup = new Array();
            $('input[name="ids[]"]:checked').each(function () {
                selectedAttrGroup.push(this.value);
            });      
        });
    });
```
细节不啰嗦了，主要在于体会。


