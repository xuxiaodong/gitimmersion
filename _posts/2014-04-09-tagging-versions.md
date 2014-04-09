---
layout: post
title: 给版本打标签
date: 2014-04-09 13:40
post-link: http://gitimmersion.com/lab_13.html
---

**目的**

学习如何使用名称给提交打标签以便将来参考。

让我们叫 hello 程序的当前版本为 version 1 (v1)。

### 标记 version 1

```
$ git tag v1
```

现在你可以引用程序的当前版本为 v1。

### 标记先前的版本

让我们标记当前版本之前的版本为 v1-beta。首先我们需要检出
先前的版本。代替查询哈希，我们将使用 `^` 来表示“v1 的父
提交”。

如果使用 `v1^` 表示法遇到问题，那么你也可以试试 `v1~1`，
这将引用相同的版本。该表示法意为“v1 的第一个祖先提交”。

```
$ git checkout v1^
$ cat hello.rb
```

```
$ git checkout v1^
Note: checking out 'v1^'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

    git checkout -b new_branch_name

HEAD is now at 582495a... Added a default value
$ cat hello.rb
name = ARGV.first || "World"

puts "Hello, #{name}!"
```

看，这是我们添加注释之前的默认值版本。让我们使它成为 v1-beta。

```
$ git tag v1-beta
```

### 按标签名检出

现在试试在两个标记版本之间切换。

```
$ git checkout v1
$ git checkout v1-beta
```

```
$ git checkout v1
Previous HEAD position was 582495a... Added a default value
HEAD is now at 1f7ec5e... Added a comment
$ git checkout v1-beta
Previous HEAD position was 1f7ec5e... Added a comment
HEAD is now at 582495a... Added a default value
```

### 使用 tag 命令查看标签

你可以使用 `git tag` 命令来看看可用的标签有什么。

```
$ git tag
```

```
$ git tag
v1
v1-beta
```

### 查看日志中的标签

你也可以检查日志中的标签。

```
$ git hist master --all
```

```
$ git hist master --all
* 1f7ec5e 2013-04-13 | Added a comment (v1, master) [Jim Weirich]
* 582495a 2013-04-13 | Added a default value (HEAD, v1-beta) [Jim Weirich]
* 323e28d 2013-04-13 | Using ARGV [Jim Weirich]
* 9416416 2013-04-13 | First Commit [Jim Weirich]
```

你可以在日志输出中看到与分支名称（master）一起列出了两
个标签（v1 和 v1-beta）。而且 HEAD 显示你当前检出的提交
（此刻是 v1-beta）。
