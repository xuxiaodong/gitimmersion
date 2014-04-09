---
layout: post
title: 获得旧版本
date: 2014-04-09 13:10
post-link: http://gitimmersion.com/lab_12.html
---

**目的**

学习如何检出工作目录中的先前快照。

在历史中回忆很容易。`checkout` 命令将从仓库复制任意快照
到工作目录。

### 获得先前版本的哈希

```
$ git hist
```

注意：你记得在 `.gitconfig` 文件中定义的 `hist`，对吗？如果
不是这样，那么回顾一下有关别名的实验。

```
$ git hist
* 1f7ec5e 2013-04-13 | Added a comment (HEAD, master) [Jim Weirich]
* 582495a 2013-04-13 | Added a default value [Jim Weirich]
* 323e28d 2013-04-13 | Using ARGV [Jim Weirich]
* 9416416 2013-04-13 | First Commit [Jim Weirich]
```

检查日志输出，并找到第一个提交的哈希。它应当在 `git hist`
输出的最后一行。在下面的命令中使用哈希码（前 7 个字符就
够了）。然后检查 hello.rb 文件的内容。

```
$ git checkout <hash>
$ cat hello.rb
```

注意：这儿给的是 Unix 命令，适用于 Mac 和 Linux 系统。不幸
的是，Windows 用户必须换成他们的原生命令。

注意：许多命令都需要仓库中的哈希值。因为你的哈希值将与我的
不同，当你看到命令中的 `<hash>` 或 `<treehash>` 时，使用你
仓库的正确哈希值替换。

你应该看到：

```
$ git checkout 9416416
Note: checking out '9416416'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

    git checkout -b new_branch_name

HEAD is now at 9416416... First Commit
$ cat hello.rb
puts "Hello, World"
```

在 Git 中的“detached HEAD”信息意味着 HEAD (Git 跟踪当前目录
应当匹配的那部分)是直接指向提交而非分支。在你没有切换到不同
的分支时，这种状态只会记得已经提交的更改。一旦你检出了新的
分支或标签，分离的提交将被丢弃 (因为 HEAD 已经移走)。如果你
想要保存在分离状态的提交，那么你需要创建分支来记住提交。

Git 的旧版本将抱怨分离的 HEAD 状态不在本地分支。现在不用担心
这种情况。

注意 hello.rb 文件是最原始的内容。

### 回到在 master 分支中的最新版本

```
$ git checkout master
$ cat hello.rb
```

你应该看到：

```
$ git checkout master
Previous HEAD position was 9416416... First Commit
Switched to branch 'master'
$ cat hello.rb
# Default is "World"
name = ARGV.first || "World"

puts "Hello, #{name}!"
```

`master` 是默认分支的名称。通过名称检出分支，你能够回到
该分支的最新版本。
