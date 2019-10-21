---
title: git版本回退
categories: git
toc: true
thumbnail: https://cdn.jsdelivr.net/gh/zzhjoker/hexo-cdn@1.2/git/git.jpg
tags:
  - git
---

- **版本回退**
  如果当前版本出现了严重的问题还可以使用`git reset`回退到想要的版本.
  **参数**  
   --hard <版本 ID>

```javascript
//回退到上一个版本
git reset --hard HEAD^
//回退到指定版本
git reset --hard 91331759bc
```

<!--more-->

- **HEAD 指针**
  git 的版本回退极快，因为 git 在内部有一个指向当前版本的`HEAD`指针，当回退版本的时候 git 仅仅是将`HEAD`指针指向了指定的版本。然后将工作区的文件更新了，所以当`HEAD`指向那个版本号，当前版本就定位到哪。

* **查看历史命令**
  `git reflog` 查看输入命令的历史记录

```javascript
  git reflog

//命令行日志
fc5f8e5 (HEAD -> dev) HEAD@{0}: commit: 基本命令
267154a HEAD@{1}: reset: moving to 267154a3a72a7431a1acfb28470482f9ba93cead
e823318 (master) HEAD@{2}: reset: moving to HEAD^
:...skipping...
fc5f8e5 (HEAD -> dev) HEAD@{0}: commit: 基本命令
267154a HEAD@{1}: reset: moving to 267154a3a72a7431a1acfb28470482f9ba93cead
e823318 (master) HEAD@{2}: reset: moving to HEAD^
9588632 HEAD@{3}: reset: moving to 9588632a99a6a0be8ba58340d6ef521f374f564f
a12138b HEAD@{4}: reset: moving to HEAD^
267154a HEAD@{5}: commit: 修改bug
a12138b HEAD@{6}: commit: add git
9588632 HEAD@{7}: commit: lesson5
e823318 (master) HEAD@{8}: checkout: moving from master to dev
e823318 (master) HEAD@{9}: checkout: moving from dev to master
e823318 (master) HEAD@{10}: checkout: moving from master to dev
e823318 (master) HEAD@{11}: checkout: moving from master to master
e823318 (master) HEAD@{12}: merge dev: Fast-forward
2ca38fb HEAD@{13}: checkout: moving from dev to master
e823318 (master) HEAD@{14}: commit: lesson3
42c1254 HEAD@{15}: commit: gitbug
2ca38fb HEAD@{16}: checkout: moving from master to dev
2ca38fb HEAD@{17}: commit: lesson2
baf7ceb HEAD@{18}: commit: lesson1
b01183d HEAD@{19}: commit: ES6
8d8d64c HEAD@{20}: commit (initial): 版本
```
