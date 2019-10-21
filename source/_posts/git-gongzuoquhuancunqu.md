---
title: 工作区和暂存区
categories: git
toc: true
thumbnail: https://cdn.jsdelivr.net/gh/zzhjoker/hexo-cdn@1.2/git/git.jpg
tags:
  - git
---

- **工作区**
  工作区就是在电脑中能看见的目录

* **暂存区**
  在工作区中有一个隐藏目录`.git`，这个隐藏的文件文件是 Git 的版本库，git 的版本库中存了很多的东西，其中最重要的称为 stage 的暂存区，还有 git 自动创建的第一条分支`master`，以及指向`master`的一个指针叫`HEAD`，而 git add 命令其实是将文件修改添加到暂存区，而 git commit 则是将暂存区中所有的文件一次性提交到当前分支。
  <!--more-->
