---
layout: post
title: 何为 Origin?
date: 2014-04-18 14:23
post-link: http://gitimmersion.com/lab_39.html
---

**目的**

学习有关命名远程仓库的内容。

```
$ git remote
```

```
$ git remote
origin
```

我们看到克隆的仓库知道远程仓库名为 origin。让我们看看是
否能获得有关 origin 的更多信息：

```
$ git remote show origin
```

```
$ git remote show origin
* remote origin
  Fetch URL: /Users/jim/working/git/git_immersion/auto/hello
  Push  URL: /Users/jim/working/git/git_immersion/auto/hello
  HEAD branch (remote HEAD is ambiguous, may be one of the following):
    greet
    master
  Remote branches:
    greet  tracked
    master tracked
  Local branch configured for 'git pull':
    master merges with remote master
  Local ref configured for 'git push':
    master pushes to master (up to date)
```

现在我们看到远程仓库“origin”简直就是原始的 hello 仓库。
远程仓库典型地存在于可能是中央服务器的独立机器上。正如
我们可以在此处看到的，它们可以指到同一机器上的仓库。关
于名称“origin”没有什么特别的，对于主中央仓库（如果有的
话）使用名称“origin”只是习惯的约定而已。
