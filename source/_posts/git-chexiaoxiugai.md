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

```javascript
  git checkout -- <filename>
```

- **撤销暂存区修改**
  `git reset` 命令既可以回退版本，也可以把暂存区的修改回退到工作区。就是将保存在暂存区中的指定文件移除，当我们用 HEAD 时，表示最新的版本。
  ```javascript
  git reset HEAD <filename>
  ```
