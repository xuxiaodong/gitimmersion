---
layout: post
title: 推送更改
date: 2014-04-18 15:50
post-link: http://gitimmersion.com/lab_48.html
---

**目的**

学习如何将更改推到远程仓库。

因为裸仓库通常共享在某种网络服务器上，所以一般很难转
到仓库中并拉下更改。因此，我们需要将更改推到其它的仓
库中。

让我们通过创建更改来开始推送。编辑 README 并提交它。

```
This is the Hello World example from the git tutorial.
(Changed in the original and pushed to shared)
```

```
$ git checkout master
$ git add README
$ git commit -m "Added shared comment to readme"
```

现在推送更改到共享的仓库。

```
$ git push shared master
```

`shared` 是接收我们推送更改的仓库名称。（记住，在上一实
验中我们已经将它添加为远程分支。）

```
$ git push shared master
To ../hello.git
   2e4c559..3923dd5  master -> master
```

注意：我们必须明确地指定接收推送的分支名称 master。它可
以设置为自动化，但我从未记住实现的命令。选择“Git Remote Branch”
gem 更易管理远程分支。
