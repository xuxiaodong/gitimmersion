---
layout: post
title: 再谈结构
date: 2014-04-11 15:47
post-link: http://gitimmersion.com/lab_21.html
---

**目的**

添加另外的文件到我们的仓库。

### 现在添加 Rakefile

让我们添加 Rakefile 到我们的仓库。下面一个恰好。

```ruby
#!/usr/bin/ruby -wKU

task :default => :run

task :run do
  require './lib/hello'
end
```

添加并提交更改。

```
$ git add Rakefile
$ git commit -m "Added a Rakefile."
```

现在你应当能够使用 Rake 来执行 hello 程序了。

```
$ rake
```

```
$ rake
Hello, World!
```
