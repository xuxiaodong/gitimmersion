---
layout: post
title: 克隆仓库
date: 2014-04-18 10:29
post-link: http://gitimmersion.com/lab_37.html
---

**目的**

学习如何创建仓库的拷贝。

### 转到工作目录

转到工作目录并创建 hello 仓库的克隆。

```
$ cd ..
$ pwd
$ ls
```

注意：现在在工作目录中。

```
$ cd ..
$ pwd
/Users/jim/working/git/git_immersion/auto
$ ls
hello
```

此刻你应当在你的工作目录，且有名为“hello”的单一仓库。

### 创建 hello 仓库的克隆

让我们创建仓库的克隆。

```
$ git clone hello cloned_hello
$ ls
```

```
$ git clone hello cloned_hello
Cloning into cloned_hello...
done.
$ ls
cloned_hello
hello
```

在你的工作目录中现在应当有两个仓库：原始的“hello”仓库
和新克隆的“cloned\_hello”仓库。
