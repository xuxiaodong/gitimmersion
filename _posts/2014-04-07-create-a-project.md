---
layout: post
title: 创建项目
date: 2014-04-07 18:58
post-link: http://gitimmersion.com/lab_03.html
---

**目的**

学习如何从零开始创建 Git 仓库。

### 创建“Hello, World”程序

在一个空的工作目录中开始，创建一个名为“hello”的空目录，
然后创建一个名为 hello.rb 且包含如下内容的文件。

```
$ mkdir hello
$ cd hello
```

文件：hello.rb

```
puts "Hello, World"
```

### 创建仓库

你现在有一个包含单个文件的目录。要从该目录创建 Git 仓库，
执行 `git init` 命令。

```
$ git init
```

输出：

```
$ git init
Initialized empty Git repository in /Users/jim/working/git/git_immersion/auto/hello/.git/
```

### 添加程序到仓库

现在让我们添加“Hello, World”程序到仓库。

```
$ git add hello.rb
$ git commit -m "First Commit"
```

你应该看到：

```
$ git add hello.rb
$ git commit -m "First Commit"
[master (root-commit) 9416416] First Commit
 1 files changed, 1 insertions(+), 0 deletions(-)
 create mode 100644 hello.rb
```
