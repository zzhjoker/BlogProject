---
title: git错误
categories: bug
toc: true
thumbnail: https://cdn.jsdelivr.net/gh/zzhjoker/hexo-cdn@1.1/error/bug1.png
tags:
  - 错误日志-webpack
---

### git 拉取时发生错误

```javascript
- branch master -> FETCH_HEAD
  fatal: refusing to merge unrelated histories

```

<!--more-->

- 错误命令：git pull origin master

* 错误原因：两条不相干的分支合并时会报错

* 解决方法：加上参数--allow-unrelated-histories，强行合并两条不相干的分支

* 解决命令： git pull origin master --allow-unrelated-histories

### git 推送时发生错误

```javascript
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

```

- 错误命令：git push -u origin master

* 错误原因：git 仓库中已有文件，本地文件推送时报错
* 解决方法：先拉取在推送 git pull origin master
