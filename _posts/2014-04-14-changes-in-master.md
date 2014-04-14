---
layout: post
title: 在 master 中更改
date: 2014-04-14 13:23
post-link: http://gitimmersion.com/lab_26.html
---

**目的**

学习如何处理包含不同（及可能有冲突）更改的多个分支。

当你更改 greet 分支时，其他人决定更新 master 分支。他们
添加了一个 README。

### 切换到 master 分支

```
$ git checkout master
```

### 创建 README

```
This is the Hello World example from the git tutorial.
```

### 提交 README 到 master

```
$ git add README
$ git commit -m "Added README"
```
