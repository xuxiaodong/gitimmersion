---
layout: post
title: 回顾克隆的仓库
date: 2014-04-18 14:09
post-link: http://gitimmersion.com/lab_38.html
---

**目的**

学习远程仓库上有关分支的内容。

### 查看克隆的仓库

让我们看一看克隆的仓库。

```
$ cd cloned_hello
$ ls
```

```
$ cd cloned_hello
$ ls
README
Rakefile
lib
```

你应当看到原始仓库的顶层目录中所有文件的列表 (README、
Rakefile 及 lib)。

### 回顾仓库历史

```
$ git hist --all
```

```
$ git hist --all
* 2fae0b2 2013-04-13 | Updated Rakefile (HEAD, origin/master, origin/greet, origin/HEAD, master) [Jim Weirich]
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

现在你应当看到新仓库的全部提交列表，而且它或多或少会
匹配原始仓库的提交历史。仅有的差异体现在分支名称上。

### 远程分支

你应当在历史列表中看到 master 分支 (孤单的 HEAD)。而且你也
将有许多奇怪的分支名称 (origin/master、origin/greet 及 origin/HEAD
)。我们一会儿将讨论它们。
