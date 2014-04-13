---
layout: post
title: Git 内幕：直接处理 Git 对象
date: 2014-04-13 15:19
post-link: http://gitimmersion.com/lab_23.html
---

**目的**

浏览对象存储的结构。学习如何使用 SHA1 哈希来查找仓库中
的内容。

现在让我们使用一些工具来直接探究 Git 对象。

### 查找最新的提交

```
$ git hist --max-count=1
```

这应当显示仓库中所做的最新提交。在你的系统中的 SHA1 
哈希也许与我的不同，但应该看起来类似。

```
$ git hist --max-count=1
* 96ee164 2013-04-13 | Added a Rakefile. (HEAD, master) [Jim Weirich]
```

### 转存最新的提交

使用上面所列提交的 SHA1 哈希。

```
$ git cat-file -t <hash>
$ git cat-file -p <hash>
```

这儿是我的输出：

```
git cat-file -t 96ee164
commit
$ git cat-file -p 96ee164
tree 096b74c56bfc6b40e754fc0725b8c70b2038b91e
parent 0f36766e05bc55d765ec8afe288430edc69fceea
author Jim Weirich <jim (at) neo.com> 1365880844 -0400
committer Jim Weirich <jim (at) neo.com> 1365880844 -0400

Added a Rakefile.
```

注意：如果你在别名实验中定义了 `type` 和 `dump` 别名，那么
你可以输入 `git type` 和 `git dump`，而不是更长的 `cat-file`
命令（我从未记住过）。

这是 `master` 分支头提交对象的转存结果。它看起来很像先前介
绍的提交对象。

### 查找 Tree

我们可以转存提交中的目录树引用。这应当是我们项目中的文件的
说明。使用上面所列“tree”那行的 SHA1 哈希。

```
$ git cat-file -p <treehash>
```

这儿是我的目录树看起来的样子……

```
$ git cat-file -p 096b74c
100644 blob 28e0e9d6ea7e25f35ec64a43f569b550e8386f90    Rakefile
040000 tree e46f374f5b36c6f02fb3e9e922b79044f754d795    lib
```

是的，我看到了 Rakefile 和 lib 目录。

### 转存 lib 目录

```
$ git cat-file -p <libhash>
```

```
$ git cat-file -p e46f374
100644 blob c45f26b6fdc7db6ba779fc4c385d9d24fc12cf72    hello.rb
```

这是 hello.rb 文件。

### 转存 hello.rb 文件

```
$ git cat-file -p <rbhash>
```

```
$ git cat-file -p c45f26b
# Default is World
# Author: Jim Weirich (jim@somewhere.com)
name = ARGV.first || "World"

puts "Hello, #{name}!"
```

你已经有它了。我们直接从 Git 仓库转存了提交对象、树对象、
以及 blob 对象。blob、树及提交就是全部了。

### 浏览你自己的 Git 仓库

手动浏览你自己的 Git 仓库。看看是否能通过遵循最新提交的
SHA1 哈希引用来从第一个提交找出最初的 hello.rb 文件。
