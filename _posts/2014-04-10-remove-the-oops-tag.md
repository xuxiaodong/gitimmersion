---
layout: post
title: Remove the oops tag
date: 2014-04-10 15:49
post-link: http://gitimmersion.com/lab_18.html
---

**目的**

移除 oops 标签（料理家务）。

### 移除 oops 标签

oops 标签已经实现其目的。让我们移除它，以便它引用的提交
被作为垃圾回收。

```
$ git tag -d oops
$ git hist --all
```

```
$ git tag -d oops
Deleted tag 'oops' (was a10293f)
$ git hist --all
* 1f7ec5e 2013-04-13 | Added a comment (HEAD, v1, master) [Jim Weirich]
* 582495a 2013-04-13 | Added a default value (v1-beta) [Jim Weirich]
* 323e28d 2013-04-13 | Using ARGV [Jim Weirich]
* 9416416 2013-04-13 | First Commit [Jim Weirich]
```

在仓库中不再列出 oops 标签了。
