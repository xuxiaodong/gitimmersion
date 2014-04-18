---
layout: post
title: 重置 master 分支
date: 2014-04-18 09:29
post-link: http://gitimmersion.com/lab_33.html
---

**目的**

重置 master 分支到冲突提交前的地方。

### 重置 master 分支

当我们添加交互模式到 master 分支时，我们所做的更改与 greet
分支中的更改冲突了。让我们倒回 master 分支中冲突更改前的地
方。这允许我们来演示变基命令而不必担心冲突。

```
$ git checkout master
$ git hist
```

```
$ git hist
* 05f32c0 2013-04-13 | Made interactive (HEAD, master) [Jim Weirich]
* b59a8c2 2013-04-13 | Added README [Jim Weirich]
* 96ee164 2013-04-13 | Added a Rakefile. [Jim Weirich]
* 0f36766 2013-04-13 | Moved hello.rb to lib [Jim Weirich]
* eb30103 2013-04-13 | Add an author/email comment [Jim Weirich]
* 1f7ec5e 2013-04-13 | Added a comment (v1) [Jim Weirich]
* 582495a 2013-04-13 | Added a default value (v1-beta) [Jim Weirich]
* 323e28d 2013-04-13 | Using ARGV [Jim Weirich]
* 9416416 2013-04-13 | First Commit [Jim Weirich]
```

“Added README”是冲突的交互模式之前的提交。我们将重置 master 
分支到“Added README”提交处。

```
$ git reset --hard <hash>
$ git hist --all
```

回顾下日志，应当看到仓库已经回到我们合并之前的时间点。

```
$ git hist --all
* b59a8c2 2013-04-13 | Added README (HEAD, master) [Jim Weirich]
| * 28917a4 2013-04-13 | Updated Rakefile (greet) [Jim Weirich]
| * 4dac415 2013-04-13 | Hello uses Greeter [Jim Weirich]
| * 39347b3 2013-04-13 | Added greeter class [Jim Weirich]
|/  
* 96ee164 2013-04-13 | Added a Rakefile. [Jim Weirich]
* 0f36766 2013-04-13 | Moved hello.rb to lib [Jim Weirich]
* eb30103 2013-04-13 | Add an author/email comment [Jim Weirich]
* 1f7ec5e 2013-04-13 | Added a comment (v1) [Jim Weirich]
* 582495a 2013-04-13 | Added a default value (v1-beta) [Jim Weirich]
* 323e28d 2013-04-13 | Using ARGV [Jim Weirich]
* 9416416 2013-04-13 | First Commit [Jim Weirich]
```
