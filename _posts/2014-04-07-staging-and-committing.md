---
layout: post
title: 暂存与提交
date: 2014-04-07 20:05
post-link: http://gitimmersion.com/lab_07.html
---

在 Git 中分开暂存步骤是直到你需要使用源码控制处理的协调
解决哲学。你可以继续对工作目录做更改，然后当你想要与源
码控制交互时，Git 允许你使用精确地记录你所作的小提交来
记录你的更改。

例如，假设你编辑了三个文件（a.rb、b.rb 及 c.rb）。现在你
想提交所有更改，但你想要 a.rb 和 b.rb 中的更改作为单个的
提交，而 c.rb 的更改与前两个文件在逻辑上不相关，那么应该
分开提交。

你可以执行下列命令：

```
$ git add a.rb
$ git add b.rb
$ git commit -m "Changes for a and b"

$ git add c.rb
$ git commit -m "Unrelated change to c"
```

通过分开暂存和提交，你能够更加容易地调优每一个提交。
