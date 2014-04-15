---
layout: post
title: 查看分叉的分支
date: 2014-04-15 10:41
post-link: http://gitimmersion.com/lab_27.html
---

**目的**

学习如何查看仓库中分叉的分支。

### 查看当前分支

在仓库中我们现在有两个分叉的分支。使用下面的 `log` 命令
来查看分支及它们如何分叉。

```
$ git hist --all
```

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

在此我们第一次有机会看到 `git hist` 中 `--graph` 选项的效果。
添加 `--graph` 到 `git hist` 使它能够使用简单的 ASCII 字符来
绘制提交树。我们可以看到两个分支（greet 和 master），并且 master
分支是当前的 HEAD。两个分支的共同祖先是“Added a Rakefile”分支。

`--all` 选项确使我们看到所有分支。默认只显示当前分支。
