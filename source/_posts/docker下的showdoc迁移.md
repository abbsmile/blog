---
title: docker下的showdoc迁移
date: 2020-03-23 18:17:24
categories:
- 运维
tags:
- docker showdoc

---

#### 原因

在公司和别人合作时，笔者比较喜欢的文档工具是`showdoc`。

- 第一：可以安装在自己的服务器上，便于掌控；
- 第二：文件权限控制等，还可以；
- 第三：可以写接口，也可以记录账号密码等一系列信息，还不错

最近，由于公司实际情况，需要换服务器，原来通过docker安装的showdoc，如何迁移到新的服务器，成为笔者的新问题。

#### 解决方式 

也不难，笔者迁移成功前后大概花了半个小时多一点。

- 备份一下

  ```shell
  [root@izwz9190o505f7toa7ffu2z ~]# docker image ls
  [root@izwz9190o505f7toa7ffu2z ~]# docker save -o showdoc.tar star7th/showdoc
  ```

- `copy` 到另一台服务器上去
- 在另一台服务器`docker run`

#### 出现的问题

拷贝过去后，发现数据没同步。笔者就直接暴力解决了：把这边docker映射的文件全部拷过去，然后开个权限。

后面个人感觉只要拷贝数据库文件就行了, 以后碰到再试试。

差不多就是这样的思路，细节部分这边先忽略了。



