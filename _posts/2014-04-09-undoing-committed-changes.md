---
layout: post
title: 撤销提交的更改
date: 2014-04-09 15:51
post-link: http://gitimmersion.com/lab_16.html
---

**目的**

学习如何还原已经提交到本地仓库的更改。

### 撤销提交

有时候你意识到已经提交的更改不正确并想撤销该提交。有
几种方式可以处理这种问题，我们在本实验中所用的方式总
是安全的。

实际上我们将通过创建新的提交来撤销原来不想要更改的提
交。

### 更改文件并提交

更改 hello.rb 文件成下列内容：

```ruby
# This is an unwanted but committed change
name = ARGV.first || "World"

puts "Hello, #{name}!"
```

```
$ git add hello.rb
$ git commit -m "Oops, we didn't want this commit"
```

### 创建还原提交

要撤销已提交的更改，我们需要创建一个提交来移除由不想
要的提交所引入的更改。

```
$ git revert HEAD
```

这将带你到编辑器中。你可以编辑默认的提交信息，或直接
离开它。保存并关闭文件。你应该看到：

```
$ git revert HEAD --no-edit
[master a10293f] Revert "Oops, we didn't want this commit"
 1 files changed, 1 insertions(+), 1 deletions(-)
```

因为我们将撤销我们做的最后提交，所以我们可以使用 `HEAD`
作为还原的参数。通过简单的指定哈希值，我们可以撤销早期
历史中的任意提交。

注意：命令中的 `--no-edit` 可被忽略。在不打开编辑器生成输
出时需要它。

### 检查日志

检查日志来显示我们仓库中不想要及还原的提交。

```
$ git hist
```

```
$ git hist
* a10293f 2013-04-13 | Revert "Oops, we didn't want this commit" (HEAD, master) [Jim Weirich]
* 838742c 2013-04-13 | Oops, we didn't want this commit [Jim Weirich]
* 1f7ec5e 2013-04-13 | Added a comment (v1) [Jim Weirich]
* 582495a 2013-04-13 | Added a default value (v1-beta) [Jim Weirich]
* 323e28d 2013-04-13 | Using ARGV [Jim Weirich]
* 9416416 2013-04-13 | First Commit [Jim Weirich]
```

这种技术将处理任何提交（虽然你可能必须解决冲突）。在
公开分享的远程仓库上使用分支更加安全。

### 下一步

接下来，让我们看看从仓库历史中移除最近提交所用的技术。
