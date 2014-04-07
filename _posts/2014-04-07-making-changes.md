---
layout: post
title: 做更改
date: 2014-04-07 19:28
post-link: http://gitimmersion.com/lab_05.html
---

**目的**

学习如何监视工作目录的状态。

### 更改“Hello, World”程序

是时候更改我们的 hello 程序以便使它能从命令行传递参数。将
文件更改为：

```
puts "Hello, #{ARGV.first}!"
```

### 检查状态

现在检查工作目录的状态。

```
$ git status
```

你应该看到：

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

值得注意的第一件事是 Git 知道 hello.rb 文件已被修改，但 Git
还没有通知这些更改。

另外要注意的是状态信息给你接下来需要做什么的提示。如
果你想要添加这些更改到仓库，那么使用 `git add` 命令。
否则，使用 `git checkout` 命令放弃更改。

### 下一步

让我们暂存更改。
