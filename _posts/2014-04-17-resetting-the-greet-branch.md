---
layout: post
title: 重置 greet 分支
date: 2014-04-17 10:23
post-link: http://gitimmersion.com/lab_32.html
---

**目的**

重置 greet 分支到第一次合并前的地方。

### 重置 greet 分支

让我们回到 greet 分支在合并 master 之前的时间点。我们可以
重置分支到我们想要的任何提交处。重点是修改分支指针以指向
提交树中的任何位置。

在本实验中，我们想要回到 greet 在与 master 合并之前的地方。
我们需要找到合并前的最后一个提交。

```
$ git checkout greet
$ git hist
```

```
$ git checkout greet
Already on 'greet'
$ git hist
*   25f0e8c 2013-04-13 | Merged master fixed conflict. (HEAD, greet) [Jim Weirich]
|\  
| * 05f32c0 2013-04-13 | Made interactive (master) [Jim Weirich]
* |   844d1ed 2013-04-13 | Merge branch 'master' into greet [Jim Weirich]
|\ \  
| |/  
| * b59a8c2 2013-04-13 | Added README [Jim Weirich]
* | 28917a4 2013-04-13 | Updated Rakefile [Jim Weirich]
* | 4dac415 2013-04-13 | Hello uses Greeter [Jim Weirich]
* | 39347b3 2013-04-13 | Added greeter class [Jim Weirich]
|/  
* 96ee164 2013-04-13 | Added a Rakefile. [Jim Weirich]
* 0f36766 2013-04-13 | Moved hello.rb to lib [Jim Weirich]
* eb30103 2013-04-13 | Add an author/email comment [Jim Weirich]
* 1f7ec5e 2013-04-13 | Added a comment (v1) [Jim Weirich]
* 582495a 2013-04-13 | Added a default value (v1-beta) [Jim Weirich]
* 323e28d 2013-04-13 | Using ARGV [Jim Weirich]
* 9416416 2013-04-13 | First Commit [Jim Weirich]
```

有点难以阅读。通过查看数据我们发现“Updated Rakefile”是
greet 分支在合并前的最后一个提交。让我们重置 greet 分支到
该提交处。

```
$ git reset --hard <hash>
```

```
$ git reset --hard 28917a4
HEAD is now at 28917a4 Updated Rakefile
```

### 检查分支

看看 greet 分支的日志。在它的历史中，我们不再有合并提交。

```
$ git hist --all
```

```
$ git hist --all
* 05f32c0 2013-04-13 | Made interactive (master) [Jim Weirich]
* b59a8c2 2013-04-13 | Added README [Jim Weirich]
| * 28917a4 2013-04-13 | Updated Rakefile (HEAD, greet) [Jim Weirich]
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
