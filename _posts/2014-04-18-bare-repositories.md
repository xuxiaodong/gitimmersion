---
layout: post
title: 裸仓库
date: 2014-04-18 15:35
post-link: http://gitimmersion.com/lab_46.html
---

**目的**

学习如何创建裸仓库。

裸仓库（没有工作目录）通常用于共享。

### 创建裸仓库

```
$ cd ..
$ git clone --bare hello hello.git
$ ls hello.git
```

注意：现在在工作目录中。

```
$ git clone --bare hello hello.git
Cloning into bare repository hello.git...
done.
$ ls hello.git
HEAD
config
description
hooks
info
objects
packed-refs
refs
```

结尾带 `.git` 的仓库习惯约定是裸仓库。我们可以看到在
hello.git 仓库中没有工作目录。实际上，除了非裸仓库的
.git 目录外什么也没有。
