---
layout: post
title: 更改而非文件
date: 2014-04-08 21:24
post-link: http://gitimmersion.com/lab_09.html
---

Git 聚焦于文件的更改而非文件本身。当你说 Git 添加文件时，
你并非在告诉 Git 要添加文件到仓库。而是说 Git 应当对文件
的当前状态做记录以便稍后提交。

我们将尝试在本次实验中探索其中的差异。

### 初次更改：允许默认名称

如果命令行参数未提供，更改“Hello, World”程序来接受一个
默认值。

```ruby
name = ARGV.first || "World"

puts "Hello, #{name}!"
```

### 添加更改

现在添加此次更改到 Git 的暂存区。

```
$ git add hello.rb
```

### 二次更改：添加注释

现在给“Hello, World”程序添加一行注释。

```ruby
# Default is "World"
name = ARGV.first || "World"

puts "Hello, #{name}!"
```

### 检查当前状态

```
$ git status
```

你应该看到：

```
$ git status
# On branch master
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#   modified:   hello.rb
#
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#   modified:   hello.rb
#
```

注意 hello.rb 在状态中被列了两次。第一次更改已被暂存，且
准备提交。第二次更改还未暂存。如果你现在提交，那么注释不
会保存到仓库中。

让我们试试看。

### 提交

提交暂存的更改，然后重新检查状态。

```
$ git commit -m "Added a default value"
$ git status
```

你应该看到：

```
$ git commit -m "Added a default value"
[master 582495a] Added a default value
 1 files changed, 3 insertions(+), 1 deletions(-)
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

`status` 命令将告诉你 hello.rb 还有未记录的更改，且不在暂存
区。

### 添加第二次更改

现在添加第二次更改到暂存区，然后执行 `git status`。

```
$ git add .
$ git status
```

注意：我们使用当前目录（.）作为要添加的文件。这是一种
添加当前目录及其子目录下所有更改文件的习惯简写方式。
但因为它添加所有东东，所以在做 `add .` 前检查状态是一
个好主意，只是为了确定你没有添加不想要的文件。

我想你已经明白了 `add .` 这个技巧，但为了安全在余下的
教程中我们将继续直接添加文件。

你应该看到：

```
$ git status
# On branch master
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#   modified:   hello.rb
#
```

现在第二次已经暂存，且准备提交。

### 提交第二次更改

```
$ git commit -m "Added a comment"
```
