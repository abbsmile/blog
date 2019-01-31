---
title: rm -rf血淋淋的例子
date: 2019-01-29 12:08:23
categories: 
- 技术心得
tags: 
- Linux
---

## 背景
群里看见一则消息，rm -rf误删系统重要文件。感觉有借鉴意义，特记录下来。

## 过程
```
rm -rf bak_2017./*
rm -rf bak_2019 ./*
```

看见没有，如果操作的比较快，多打了个空格，会造成无法挽回的损失。

熟手在rm -rf 上犯错屡见不鲜。

## 结论

能不用就不用。windows上垃圾箱的发明确有创造性意义。

[Trash-cli : A Commandline Trashcan For Unix-like Systems](https://www.ostechnix.com/trash-cli-command-line-trashcan-unix-like-systems/) 不错，可试用一下。

