---
layout: post
title: 修正提交
date: 2014-04-11 15:18
post-link: http://gitimmersion.com/lab_19.html
---

**目的**

学习如何修正现有的提交。

### 更改程序并提交

给程序添加作者注释。

```ruby
# Default is World
# Author: Jim Weirich
name = ARGV.first || "World"

puts "Hello, #{name}!"
```

```
$ git add hello.rb
$ git commit -m "Add an author comment"
```

### 唉，该有 Email 啊

在你做了提交之后，你意识到任何好的作者注释都应该包含
Email 地址。更新 hello 程序来包含 Email。

```ruby
# Default is World
# Author: Jim Weirich (jim@somewhere.com)
name = ARGV.first || "World"

puts "Hello, #{name}!"
```

### 修正先前的提交

我们真的不想因为 Email 而分开提交。让我们修正先前的提交
来包含 Email 更改。

```
$ git add hello.rb
$ git commit --amend -m "Add an author/email comment"
```

```
$ git add hello.rb
$ git commit --amend -m "Add an author/email comment"
[master eb30103] Add an author/email comment
 1 files changed, 2 insertions(+), 1 deletions(-)
```

### 回顾历史

```
$ git hist
```

```
$ git hist
* eb30103 2013-04-13 | Add an author/email comment (HEAD, master) [Jim Weirich]
* 1f7ec5e 2013-04-13 | Added a comment (v1) [Jim Weirich]
* 582495a 2013-04-13 | Added a default value (v1-beta) [Jim Weirich]
* 323e28d 2013-04-13 | Using ARGV [Jim Weirich]
* 9416416 2013-04-13 | First Commit [Jim Weirich]
```

我们可以看到最初的“author”提交现在消失了，而且它已经
被“author/email”提交替换。通过重置分支到某个提交并重
新提交新的更改，你可以实现相同的效果。
