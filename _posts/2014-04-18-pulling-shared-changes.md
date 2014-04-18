---
layout: post
title: 拉下共享的更改
date: 2014-04-18 16:06
post-link: http://gitimmersion.com/lab_49.html
---

**目的**

学习如何从共享的仓库拉下更改。

迅速跳过克隆仓库，且让我们拉下刚才推送到共享仓库的更
改。

```
$ cd ../cloned_hello
```

注意：现在在 cloned\_hello 仓库中。

继续处理……

```
$ git remote add shared ../hello.git
$ git branch --track shared master
$ git pull shared master
$ cat README
```
