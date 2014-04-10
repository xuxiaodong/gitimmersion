---
layout: post
title: 从分支移除提交
date: 2014-04-10 10:18
post-link: http://gitimmersion.com/lab_17.html
---

**目的**

学习如何从分支移除最近的提交。

上一小节的 `revert` 是一个让我们撤销仓库中的任意提交的强
大命令。然而，原始提交和“撤销”提交在分支历史中都可见（使
用 `git log` 命令）。

我们经常做提交，并很快意识到犯了错误。如果有一个“收回”命
令能允许我们假装不正确的提交从未发生过该多好啊。“收回”命
令甚至还会阻止错误的提交在 `git log` 历史中的显示。这就
像错误的提交从未发生过一样。

### 重置命令

我们已经介绍过 `reset` 命令，并用它来设置暂存区以便与特
定的提交保持一致（我们在之前的实验中使用 `HEAD` 提交）。

当给定提交引用（如哈希、分支或标签名）时，`reset` 命令
将：

* 重写当前分支到指向的特定提交
* 重置暂存区到匹配特定的提交（可选）
* 重置工作目录到匹配特定的提交（可选）

### 检查历史

让我们快速的检查我们的提交历史。

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

我们看到在该分支中的最后两个提交为“Oops”和“Revert Oops”。
让我们使用 `reset` 来移除它们。

### 首先，标记分支

但在我们移除提交前，让我们使用一个标签来标记最新的提
交以便能够再次找到它。

```
$ git tag oops
```

### 重置到 Oops 前

看看上面的日志历史，我们将知道标记为“v1”的提交是错误
提交之前的正确提交。让我们重置分支到该位置。因为分支
已经标记，所以我们可以在 `reset` 命令中使用标签名（
如果它没有被标记，那么我们只能使用哈希值）。

```
$ git reset --hard v1
$ git hist
```

```
$ git reset --hard v1
HEAD is now at 1f7ec5e Added a comment
$ git hist
* 1f7ec5e 2013-04-13 | Added a comment (HEAD, v1, master) [Jim Weirich]
* 582495a 2013-04-13 | Added a default value (v1-beta) [Jim Weirich]
* 323e28d 2013-04-13 | Using ARGV [Jim Weirich]
* 9416416 2013-04-13 | First Commit [Jim Weirich]
```

我们的 master 分支现在指到 v1 提交，并且 Oops 和 Revert Oops 提
交已经不在分支中。`--hard` 参数表示应当更新工作目录以便与新的分
支头保持一致。

### 什么也没丢

但错误的提交发生了什么？结果是提交仍然在仓库中。事实上，我们仍然
能够引用它们。记得在本实验开始我们使用标签“oops”标记了还原的提交。
让我们看看所有的提交。

```
$ git hist --all
```

```
$ git hist --all
* a10293f 2013-04-13 | Revert "Oops, we didn't want this commit" (oops) [Jim Weirich]
* 838742c 2013-04-13 | Oops, we didn't want this commit [Jim Weirich]
* 1f7ec5e 2013-04-13 | Added a comment (HEAD, v1, master) [Jim Weirich]
* 582495a 2013-04-13 | Added a default value (v1-beta) [Jim Weirich]
* 323e28d 2013-04-13 | Using ARGV [Jim Weirich]
* 9416416 2013-04-13 | First Commit [Jim Weirich]
```

在这儿我们看到错误的提交并没有消失。它们仍然在仓库中。它们只是不再
列到 master 分支中。如果我们没有标记它们，它们依然在仓库中，但除了
使用哈希值外没有别的方法引用它们。未引用的提交保留在仓库中，一直到
系统运行垃圾回收软件时。

### 重置的危险性

在本地分支上重置一般是安全的。任何“事故”通常都能通过重置到想要的提
交来恢复。

然而，如果分支在共享的远程仓库上，那么重置可能使其他用户共享的分支
混乱。
