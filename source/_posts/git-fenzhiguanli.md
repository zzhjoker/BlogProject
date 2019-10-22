---
title: git分支管理
categories: git
toc: true
thumbnail: https://cdn.jsdelivr.net/gh/zzhjoker/hexo-cdn@1.2/git/git.jpg
tags:
  - git
---

分支管理是 git 中一个非常强大的功能，在开发中通常是有一个稳定的主分支，和一个开发的 dev 分支，在保证主分支稳定的情况下不断的在 dev 分支上增加新功能，直到功能开发完毕在合并到主分支上，这样既安全又不会因为某些测试功能影响到其他人的开发工。

- **创建分支**
  使用 git branch dev 创建一条新的分支

```javascript
  git branch dev

  //创建dev分支并切换到dev分支上
  git checkout -b dev
```

- **切换分支**
  使用 git checkout dev 切换到指定分支
  ```javascript
  git checkout dev
  ```

* **删除分支**
  使用 git branch -d 删除的指定分支

  ```javascript
  git branch -d dev
  //强行删除为合并的分支
  git branch -D dev

  ```

- **合并分支**
  使用 git merge dev 将 dev 合并到当前主分支

  ```javascript
  git merge dev
  git merge --no-ff -m "版本信息" dev
  ```

* **查看分支合并**
  用带参数的 git log 可以看到分支的合并情况

```javascript
 git log --graph --pretty=oneline --abbrev-commit
```

- **解决冲突**
  如果合并的过程中发生了冲突必须手动解决冲突

- **Bug 分支**
  当修复一个 bug 时但是 dev 中正在进行的工作还未提交，但是并不想提交，想临时创建一个分支进行修复 bug，git stash 就是先将当前分支未提交的代码封存起来，恢复成版本库最新的版本。

  ```javascript
  //将当前分支未提交内容封存
  git stash
  //查看bug分支
  git stash list
  //恢复成正常分支（封存前的状态）
  git stash apply
  //恢复成正常分支（封存前的状态），并删除stash内容
  git stash pop
  ```

  如果 bug 存在于 master 分支上，那么势必 dev 开发分支也会有相同的 bug，但是目前我们是在 master 分支上修改的这个 bug，想要将修改 bug 处合并到当前的 dev 分支上，但是却不想将 dev 分支和 master 分支进行合并，可以使用 git cherry-pick <commit>命令，把 bug 提交的修改复制到当前分支上。

  ```javascript
  git cherry-pick 4c805e2
  ```
