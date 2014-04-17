---
layout: post
title: 创建冲突
date: 2014-04-17 09:32
post-link: http://gitimmersion.com/lab_29.html
---

**目的**

在 master 分支中创建一个冲突更改。

### 切换到 master 并创建冲突

切换到 master 分支并做这个更改：

```
$ git checkout master
```

文件：lib/hello.rb

```ruby
puts "What's your name"
my_name = gets.strip

puts "Hello, #{my_name}!"
```

```
$ git add lib/hello.rb
$ git commit -m "Made interactive"
```

### 查看分支

```
$ git hist --all
```

```
$ git hist --all
*   844d1ed 2013-04-13 | Merge branch 'master' into greet (greet) [Jim Weirich]
|\  
* | 28917a4 2013-04-13 | Updated Rakefile [Jim Weirich]
* | 4dac415 2013-04-13 | Hello uses Greeter [Jim Weirich]
* | 39347b3 2013-04-13 | Added greeter class [Jim Weirich]
| | * 05f32c0 2013-04-13 | Made interactive (HEAD, master) [Jim Weirich]
| |/  
| * b59a8c2 2013-04-13 | Added README [Jim Weirich]
|/  
* 96ee164 2013-04-13 | Added a Rakefile. [Jim Weirich]
* 0f36766 2013-04-13 | Moved hello.rb to lib [Jim Weirich]
* eb30103 2013-04-13 | Add an author/email comment [Jim Weirich]
* 1f7ec5e 2013-04-13 | Added a comment (v1) [Jim Weirich]
* 582495a 2013-04-13 | Added a default value (v1-beta) [Jim Weirich]
* 323e28d 2013-04-13 | Using ARGV [Jim Weirich]
* 9416416 2013-04-13 | First Commit [Jim Weirich]
```

master 在提交“Added README”时合并到 greet 分支，但现在 master
上有一个另外的提交还没有合并回 greet。

### 下一步

在 master 中的最新更改与 greet 中现有的更改冲突了。接下来
我们将解决这些更改。
