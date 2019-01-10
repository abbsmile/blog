---
title: 放弃rm -rf 命令
date: 2019-01-01 21:28:22
tags:
---

	这个命令太危险，还是少用为好。

代替品：Trash-cli

Linux上好像安装也挺容易，笔者直接用`brew`安装，方便的很。

这篇文章介绍的很详细：
[Trash-cli : A Commandline Trashcan For Unix-like Systems](https://www.ostechnix.com/trash-cli-command-line-trashcan-unix-like-systems/)

简而言之：
```
trash-put – Delete files and folders.
trash-empty – Empty the trashcan.
trash-list – List deleted files and folders.
trash-restore – Restore a trashed file or folder.
trash-rm – Remove individual files from the trashcan.
```

命令太多，可以在`.bash_profile`文件里：
```
alias tp='trash-put'
alias te='trash-empty'
alias tl='trash-list'
alias trestory='trash-restore'
alias tr='trash-rm'
```

完美的一塌糊涂。

有些东西就是这样，感觉用的不顺手，找个工具。。真不行，自己写个小工具。。。不过大部分东西网上都有现成的轮子，用着就行了，没必要自己造。

结束！

