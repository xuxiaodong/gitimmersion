---
layout: post
title: 添加跟踪的分支
date: 2014-04-18 15:27
post-link: http://gitimmersion.com/lab_45.html
---

**目的**

学习如何添加跟踪远程分支的本地分支。

包含 `remotes/origin` 开头的分支是来自原始仓库的分支。注意
你没有叫 greet 的分支，但它知道原始仓库有 greet 分支。

### 添加跟踪远程分支的本地分支

```
$ git branch --track greet origin/greet
$ git branch -a
$ git hist --max-count=2
```

```
$ git branch --track greet origin/greet
Branch greet set up to track remote branch greet from origin.
$ git branch -a
  greet
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/greet
  remotes/origin/master
$ git hist --max-count=2
* 2e4c559 2013-04-13 | Changed README in original repo (HEAD, origin/master, origin/HEAD, master) [Jim Weirich]
* 2fae0b2 2013-04-13 | Updated Rakefile (origin/greet, greet) [Jim Weirich]
```

我们现在可以在分支列表和日志中看到 greet 分支。
