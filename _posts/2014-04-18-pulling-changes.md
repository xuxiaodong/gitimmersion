---
layout: post
title: 拉下更改
date: 2014-04-18 15:19
post-link: http://gitimmersion.com/lab_44.html
---

**目的**

学习 `git pull` 等价于 `git fetch` 和 `git merge`。

### 讨论

我们不会创建另外的更改过程并再次拉下它，而是做你想要
知道的做法：

```
$ git pull
```

等价于以下两步：

```
$ git fetch
$ git merge origin/master
```
