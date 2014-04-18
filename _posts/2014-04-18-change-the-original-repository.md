---
layout: post
title: 更改原始仓库
date: 2014-04-18 14:49
post-link: http://gitimmersion.com/lab_41.html
---

**目的**

对原始仓库做些更改以便我们可以尝试拉下更改。

### 在原始的 hello 仓库中做更改

```
$ cd ../hello
# (You should be in the original hello repository now)
```

注意：现在在 hello 仓库中。

对 README 做下列更改：

```
This is the Hello World example from the git tutorial.
(changed in original)
```

现在添加并提交此更改。

```
$ git add README
$ git commit -m "Changed README in original repo"
```

### 下一步

原始的仓库现在有克隆版本中所没有的更改。接下来我们将
拉下这些更改到克隆的仓库中。
