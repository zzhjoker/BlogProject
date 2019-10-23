---
title: git多人协作
categories: git
toc: true
thumbnail: https://cdn.jsdelivr.net/gh/zzhjoker/hexo-cdn@1.2/git/git.jpg
tags:
  - git
---

- **git 生成 sshkey**
  生成 sshkey 将 sshkey 添加到远程仓库中

  ```javascript
    ssh-keygen -t rsa -C "name.email"
  ```

<!--more-->

- **关联远程仓库**
  将本地仓库与远程仓库进行关联，每个本地仓库只可以关联一个远程仓库，origin 是默认的远程仓库名称，当然也可以修改为其他的名称。

  ```javascript
  git remote add origin <仓库地址>
  ```

* **查看远程仓库信息**
  如果没有与远程仓库进行关联将不会显示任何信息

  ```javascript
  //查看远程仓库
  git remote
  //查看更详细信息
  git remote -v
  ```

- **克隆本地仓库**
  将远程仓库克隆一份到本地仓库
  ```javascript
  git clone <远程仓库地址>
  ```
- **推送本地仓库**
  将本地仓库推送到远程仓库，加上`-u`参数，Git 不但会把本地的 maser 分支内容推送到远程新 master 分支，还会把本地的 master 分支和远程的 master 分支关联起来。

  ```javascript
  //第一次推送
  git push -u origin master

  //第二次简化命令推送
  git push origin master
  ```

- **拉取远程仓库**
  如果远程仓库中有内容，而本地仓库中也有内容，就必须先拉取在推送

  ```javascript
  git pull origin master
  //如果拉取发生了错误，可以使用参数，将两条不相干的分支强行合并
  git pull origin master --allow-unrelated-histories
  ```

  add test
