---
layout: post
title: 合并回 master
date: 2014-04-18 10:01
post-link: http://gitimmersion.com/lab_35.html
---

**目的**

我们已经保持 greet 分支与 master 最新（通过变基），现在让
我们合并 greet 中的更改回到 master 分支。

### 合并 greet 到 master 中

```
$ git checkout master
$ git merge greet
```

```
$ git checkout master
Switched to branch 'master'
$
$ git merge greet
Updating b59a8c2..2fae0b2
Fast-forward
 Rakefile       |    2 +-
 lib/greeter.rb |    8 ++++++++
 lib/hello.rb   |    6 ++++--
 3 files changed, 13 insertions(+), 3 deletions(-)
 create mode 100644 lib/greeter.rb
```

因为 master 的头是 greet 分支头的直接祖先，所以 Git 可以做
快进合并。当快进时，分支指针简单地前进到与 greet 分支相同
的提交处。

在快进合并中从来不会冲突。

### 回顾日志

```
$ git hist
```

```
$ git hist
* 2fae0b2 2013-04-13 | Updated Rakefile (HEAD, master, greet) [Jim Weirich]
* 1c23048 2013-04-13 | Hello uses Greeter [Jim Weirich]
* 62d7ce0 2013-04-13 | Added greeter class [Jim Weirich]
* b59a8c2 2013-04-13 | Added README [Jim Weirich]
* 96ee164 2013-04-13 | Added a Rakefile. [Jim Weirich]
* 0f36766 2013-04-13 | Moved hello.rb to lib [Jim Weirich]
* eb30103 2013-04-13 | Add an author/email comment [Jim Weirich]
* 1f7ec5e 2013-04-13 | Added a comment (v1) [Jim Weirich]
* 582495a 2013-04-13 | Added a default value (v1-beta) [Jim Weirich]
* 323e28d 2013-04-13 | Using ARGV [Jim Weirich]
* 9416416 2013-04-13 | First Commit [Jim Weirich]
```

greet 和 master 分支现在相同了。
