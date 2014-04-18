---
layout: post
title: 取得更改
date: 2014-04-18 14:56
post-link: http://gitimmersion.com/lab_42.html
---

**目的**

学习如何从远程仓库拉下更改。

```
$ cd ../cloned_hello
$ git fetch
$ git hist --all
```

注意：现在在 cloned\_hello 仓库中。

```
$ git fetch
From /Users/jim/working/git/git_immersion/auto/hello
   2fae0b2..2e4c559  master     -> origin/master
$ git hist --all
* 2e4c559 2013-04-13 | Changed README in original repo (origin/master, origin/HEAD) [Jim Weirich]
* 2fae0b2 2013-04-13 | Updated Rakefile (HEAD, origin/greet, master) [Jim Weirich]
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

在此刻，仓库具有来自原始仓库的全部提交，但它并没有整
合到克隆仓库的本地分支中。

在上面的历史中找到“Changed README in original repo”。
注意提交包括“origin/master”和“origin/HEAD”。

现在看看“Updated Rakefile”提交。你将看到本地 master
分支指到了此提交，并非我们取得的新提交。

`git fetch` 命令的结果将从远程仓库取得新的提交，但它
不会将这些提交合并到本地分支中。

### 检查 README

我们可以验证克隆的 README 没有被更改。

```
$ cat README
```

```
$ cat README
This is the Hello World example from the git tutorial.
```

看，没有更改。
