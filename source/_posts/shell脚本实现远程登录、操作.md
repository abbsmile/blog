---
title: shell脚本实现远程登录、操作
date: 2019-03-02 18:47:26
categories:
- Shell
tags:
- Shell
---


之前把这个名称写上了，一直没有机会填内容。算了，直接贴个代码吧！以后有时间，还是要一步一步的算清楚。

```
#!/bin/bash  

ssh -tt -i /Users/abao/.ssh/id_rsa root@139.196.98.111 << remotessh
cd /var/www/html/Hexo_blog
git pull
exit
remotessh 
```

然后，再通过本地脚本调用这个文件，可轻易实现一连串的动作。

Shell脚本这东西，不光要用在工作上。能简化自己的工作流程，尽量减化。