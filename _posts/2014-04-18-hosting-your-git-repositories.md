---
layout: post
title: 托管你的 Git 仓库
date: 2014-04-18 16:14
post-link: http://gitimmersion.com/lab_50.html
---

**目的**

学习如何设置 Git 服务器以共享仓库。

有很多方式来通过网络共享 Git 仓库。此处是“急就章”方式。

### 启动 Git 服务器

```
# (From the work directory)
$ git daemon --verbose --export-all --base-path=.
```

现在，在分开的终端窗口中，转到你的工作目录。

```
# (From the work directory)
$ git clone git://localhost/hello.git network_hello
$ cd network_hello
$ ls
```

你应当看到 hello 项目的拷贝。
