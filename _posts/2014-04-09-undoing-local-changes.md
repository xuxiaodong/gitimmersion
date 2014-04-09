---
layout: post
title: 撤销本地更改（在暂存前）
date: 2014-04-09 14:59
post-link: http://gitimmersion.com/lab_14.html
---

**目的**

学习如何还原工作目录中的更改。

### 检出 Master

在处理之前确认你在 master 中的最新提交上。

```
$ git checkout master
```

### 更改 hello.rb

有时候你修改了本地工作目录中的文件，且想要还原已经提交
的内容。`checkout` 命令可以用来处理这种情况。

更改 hello.rb 让其具有错误的注释。

```ruby
# This is a bad comment.  We want to revert it.
name = ARGV.first || "World"

puts "Hello, #{name}!"
```

### 检查状态

首先，检查工作目录的状态。

```
$ git status
```

```
$ git status
# On branch master
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#   modified:   hello.rb
#
no changes added to commit (use "git add" and/or "git commit -a")
```

我们看到 hello.rb 已被修改，但还没有暂存。

### 还原工作目录中的更改

使用 `checkout` 命令来检出 hello.rb 在仓库中的版本。

```
$ git checkout hello.rb
$ git status
$ cat hello.rb
```

```
$ git checkout hello.rb
$ git status
# On branch master
nothing to commit (working directory clean)
$ cat hello.rb
# Default is "World"
name = ARGV.first || "World"

puts "Hello, #{name}!"
```

`status` 命令显示在工作目录中没有未完成的更改。而且“错
误的注释”也不再成为文件内容的一部分。
