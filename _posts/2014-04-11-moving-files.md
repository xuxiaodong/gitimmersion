---
layout: post
title: Moving Files
date: 2014-04-11 15:32
post-link: http://gitimmersion.com/lab_20.html
---

**目的**

学习如何移动在仓库里的文件。

### 将 hello.rb 文件移到 lib 目录

我们现在将构建我们的小仓库结构。让我们将程序移到 lib 
目录。

```
$ mkdir lib
$ git mv hello.rb lib
$ git status
```

```
$ mkdir lib
$ git mv hello.rb lib
$ git status
# On branch master
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#   renamed:    hello.rb -> lib/hello.rb
#
```

通过使用 Git 来移动文件，我们通知了 Git 两件事：

1. 文件 hello.rb 已被删除。
2. 文件 lib/hello.rb 已被创建。

这些信息被立即暂存并准备提交。`git status` 命令将报告文件
已被移动。

### 移动文件另一法

关于 Git 的好事之一是你可以暂时忘掉源码控制直到准备开始提
交代码。如果我们使用系统命令代替 Git 命令来移动文件会发生
什么呢？

请与我们执行的命令集保持一致。虽然工作有点多，但结果是相同。

我们已经完成：

```
$ mkdir lib
$ mv hello.rb lib
$ git add lib/hello.rb
$ git rm hello.rb
```

### 提交新的目录

让我们提交此次移动操作。

```
$ git commit -m "Moved hello.rb to lib"
```
