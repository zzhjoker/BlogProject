---
title: 工作区和暂存区
categories: git
toc: true
thumbnail: https://cdn.jsdelivr.net/gh/zzhjoker/hexo-cdn@1.2/git/git.jpg
tags:
  - git
---

- **工作区**
  工作区就是在电脑中能正常看见的目录
  <div align="center">
    <img src=" https://cdn.jsdelivr.net/gh/zzhjoker/hexo-cdn@1.3/git/0.png">
  </div>
   <!--more-->

* **版本库**
  在工作区中有一个隐藏目录`.git`，这个隐藏的文件文件是 Git 的版本库，git 的版本库中存了很多的东西，其中最重要的称为 stage 的暂存区，还有 git 自动创建的第一条分支`master`，以及指向`master`的一个指针叫`HEAD`。

  <div align="center">
    <img src=" https://cdn.jsdelivr.net/gh/zzhjoker/hexo-cdn@1.3/git/0.jpg">
  </div>

* **暂存区**
  在版本库中还保存着暂存区，git 存储文件都是先 git add 将修改的文件提交到暂存区，在使用 git commit 将暂存区中所有文件一次性提交到当前的分支。可以理解为待提交的文件通通的都放在暂存区，然后一次性提交所有暂存区修改。
  ```javascript
  git add .
  ```
   <div align="center">
     <img src=" https://cdn.jsdelivr.net/gh/zzhjoker/hexo-cdn@1.3/git/0 (1).jpg">
   </div>
   ```javascript
   git commit -m "Hello World"
   ```
  <div align="center">
     <img src=" https://cdn.jsdelivr.net/gh/zzhjoker/hexo-cdn@1.3/git/0 (2).jpg">
   </div>
