---
layout: post
title: 导航分支
date: 2014-04-14 13:15
post-link: http://gitimmersion.com/lab_25.html
---

**目的**

学习如何导航仓库的分支。

现在在你的项目中具有两个分支：

```
$ git hist --all
```

```
$ git hist --all
* 28917a4 2013-04-13 | Updated Rakefile (HEAD, greet) [Jim Weirich]
* 4dac415 2013-04-13 | Hello uses Greeter [Jim Weirich]
* 39347b3 2013-04-13 | Added greeter class [Jim Weirich]
* 96ee164 2013-04-13 | Added a Rakefile. (master) [Jim Weirich]
* 0f36766 2013-04-13 | Moved hello.rb to lib [Jim Weirich]
* eb30103 2013-04-13 | Add an author/email comment [Jim Weirich]
* 1f7ec5e 2013-04-13 | Added a comment (v1) [Jim Weirich]
* 582495a 2013-04-13 | Added a default value (v1-beta) [Jim Weirich]
* 323e28d 2013-04-13 | Using ARGV [Jim Weirich]
* 9416416 2013-04-13 | First Commit [Jim Weirich]
```

### 切换到 master 分支

要在分支间切换，只需使用 `git checkout` 命令。

```
$ git checkout master
$ cat lib/hello.rb
```

```
$ git checkout master
Switched to branch 'master'
$ cat lib/hello.rb
# Default is World
# Author: Jim Weirich (jim@somewhere.com)
name = ARGV.first || "World"

puts "Hello, #{name}!"
```

你现在在 master 分支上。你可以判断 hello.rb 文件是否使用 
Greeter 类。

### 回到 Greet 分支

```
$ git checkout greet
$ cat lib/hello.rb
```

```
$ git checkout greet
Switched to branch 'greet'
$ cat lib/hello.rb
require 'greeter'

# Default is World
name = ARGV.first || "World"

greeter = Greeter.new(name)
puts greeter.greet
```

`lib/hello.rb` 的内容确定我们回到了 greet 分支上。
