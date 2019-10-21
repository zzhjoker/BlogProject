---
title: git基本命令
categories: git
toc: true
thumbnail: https://cdn.jsdelivr.net/gh/zzhjoker/hexo-cdn@1.2/git/git.jpg
tags:
  - git
---

- **查看 git 版本**
  查看当前 git 版本测试 git 是否安装成功

```javascript
  git version
```

- **添加用户名**
  因为 git 是分布式管理，所以每个电脑必须自报家门

```javascript

git config --global user.email "用户邮箱"
git config --global user.name "用户名"

```

- **初始化版本库**
  将当前文件夹下所有文件交给 git 管理，在当前文件下会生成`.git` 文件，这个文件一般是隐藏的，如果功力不够还是不要碰它为好。

```javascript
git init
//注意版本库只能追踪文本文件的改动，但是无法追踪图片等文件
```

- **提交文件**
  将文件提交到版本库需要两步，先将文件提交到暂存区，然后在将暂存区文件提交到版本库。

```javascript
//1，将文件提交到暂存区
  git add <file> //将单个文件提交到暂存区
  git add .        //将所有文件提交到暂存区

//2，将暂存区的文件提交到版本库
  git commit -m <message>
```

- **查看仓库状态**
  `git status`命令可以让我们查看当前状态，它会告诉我们那些文件被修改过，但还没有准备提交的修改

```javascript
git status
```

- **查看修改文件**
  `git diff`查看当前文件被修改的地方

```javascript
git diff [filename]
git diff

//命令行日志
+^M
+- **查看提交日志**^M
+  `git log`查看版本提交日志，包括时间，作者，版本号(q 退出命令模式，y 回退)^M
+  - 参数^M
+    只显示各个版本 ID^M
+    --pretty=oneline^M
+^M
```

- **查看提交日志**
  `git log`查看版本提交日志，包括时间，作者，版本号(q 退出命令模式，y 回退)
  - 参数
    只显示各个版本 ID
    --pretty=oneline

```javascript
git log


//命令行日志
commit 267154a3a72a7431a1acfb28470482f9ba93cead (HEAD -> dev)
Author: zouzenghu <zouzenghu@163.com>
Date:   Mon Oct 21 19:20:24 2019 +0800

    修改bug

commit a12138b2fd20627db5ff23aeeb7824f6ff11ea23
Author: zouzenghu <zouzenghu@163.com>
Date:   Mon Oct 21 19:19:11 2019 +0800

    add git

commit 9588632a99a6a0be8ba58340d6ef521f374f564f
Author: zouzenghu <zouzenghu@163.com>
Date:   Mon Oct 21 16:28:00 2019 +0800

    lesson5

commit e8233180e552d08d6a61c666a8d725a3b7c280f5 (master)
Author: zouzenghu <zouzenghu@163.com>
Date:   Mon Oct 21 11:36:25 2019 +0800

    lesson3
```

```javascript
git log --pretty=oneline


//命令行信息
267154a3a72a7431a1acfb28470482f9ba93cead (HEAD -> dev) 修改bug
a12138b2fd20627db5ff23aeeb7824f6ff11ea23 add git
9588632a99a6a0be8ba58340d6ef521f374f564f lesson5
e8233180e552d08d6a61c666a8d725a3b7c280f5 (master) lesson3
42c125418ff6c84f7480231a2507f5f078defdb7 gitbug
```
