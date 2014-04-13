---
layout: post
title: Git 内幕：.git 目录
date: 2014-04-13 14:33
post-link: http://gitimmersion.com/lab_22.html
---

**目的**

学习有关 .git 目录结构的内容。

### .git 目录

是时候做些浏览了。首先，从你的项目根目录开始……

```
$ ls -C .git
```

```
$ ls -C .git
COMMIT_EDITMSG  ORIG_HEAD   hooks       logs        rr-cache
HEAD        config      index       objects
MERGE_RR    description info        refs
```

这是全部 Git 东东所存储的魔法目录。让我们一瞥对象目录。

### 对象存储

```
$ ls -C .git/objects
```

```
$ ls -C .git/objects
09  1f  27  43  69  83  97  af  e4  info
0f  22  28  58  6b  94  9c  b5  e7  pack
11  24  32  59  78  96  a1  c4  eb
```

你应当看到一串包含两个字符名称的目录。目录名称是 Git 中
对象存储的 sha1 哈希的开头两个字符。

### 深入对象存储

```
$ ls -C .git/objects/<dir>
```

```
$ ls -C .git/objects/09
6b74c56bfc6b40e754fc0725b8c70b2038b91e  9fb6f9d3a104feb32fcac22354c4d0e8a182c1
```

看看两字符目录的其中之一。你应当看到一些具有 38 个字符
名称的文件。这些是 Git 中包含对象存储的文件。这些文件
已被压缩和编码，所以直接查看它们的内容并没有什么用处，
但我们将看一点。

### 配置文件

```
$ cat .git/config
```

```
$ cat .git/config
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
    ignorecase = true
[user]
    name = Jim Weirich
    email = jim (at) neo.com
```

这是项目级配置文件。在这儿的配置条目将覆盖你的主目录
中 .gitconfig 文件中的配置条目，至少对此项目来说是如
此。

### 分支与标签

```
$ ls .git/refs
$ ls .git/refs/heads
$ ls .git/refs/tags
$ cat .git/refs/tags/v1
```

```
$ ls .git/refs
heads
tags
$ ls .git/refs/heads
master
$ ls .git/refs/tags
v1
v1-beta
$ cat .git/refs/tags/v1
1f7ec5eaa8f37c2770dae3b984c55a1531fcc9e7
```

你应当认识标签子目录中的文件。每个文件都与你先前使用
`git tag` 命令所创建的标签相应。它的内容是绑定到标签
的提交哈希。

`heads` 目录与此相似，但它是用于分支而非标签。现在我
们只有一个分支，所以你在该目录中只会看到 master。

### HEAD 文件

```
$ cat .git/HEAD
```

```
$ cat .git/HEAD
ref: refs/heads/master
```

HEAD 文件包含当前分支的引用。此刻它是对于 master 的引用。
