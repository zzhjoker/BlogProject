---
title: git撤销和修改
categories: git
toc: true
thumbnail: https://cdn.jsdelivr.net/gh/zzhjoker/hexo-cdn@1.2/git/git.jpg
tags:
  - git
---

- **丢弃工作区修改**
  `git checkout -- <filename>`命令有两种状态
  一种是指定文件自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；
  一种是指定文件已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。
  <!--more-->

```javascript
  git checkout -- <filename>
```

- **撤销暂存区修改**
  `git reset` 命令既可以回退版本，也可以把暂存区的修改回退到工作区。就是将保存在暂存区中的指定文件移除，当我们用 HEAD 时，表示最新的版本。
  ```javascript
  git reset HEAD <filename>
  ```

* **删除版本库文件**
  当我们将工作区中的文件删除后，但是版本库中的文件没有删除则会造成版本不一致，使用 git status 会告诉我们那个文件被删除，如果确实要删除文件就需要将版本库中对应的文件也删除，使用 git rm <filename>，并使用 commit 在提交一次。

```javascript
  git rm source\_posts\test.md
  git commit -m "remote test.md"
```

- **恢复工作区文件**
  如果我们误删工作区中的文件，但是版本库中有留存一份，这个时候可以使用 git checkout -- <filename>来恢复，如果版本库中没有则无法被恢复。
  ```javascript
  git checkout -- source\_posts\test.md
  ```
