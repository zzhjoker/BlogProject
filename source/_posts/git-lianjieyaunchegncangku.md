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
PS D:\webCode> git status
On branch dev
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        source/_posts/git-gitVSsvn.md
        source/_posts/git-lianjieyaunchegncangku.md
```
