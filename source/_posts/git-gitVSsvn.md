---
title: git VS svn
categories: git
toc: true
thumbnail: https://cdn.jsdelivr.net/gh/zzhjoker/hexo-cdn@1.2/git/git.jpg
tags:
  - git VS svn
---

> SVN 是集中式的版本控制系统，版本库是集中存放在中央服务器的，而实际写代码时用的都是自己的电脑，所以就现需要从中央服务器上获得最新的版本，然后开始写代码，完成任务后在将自己完成的工作推送到中央服务器。让中央服务器来管理代码的版本。集中式控制系统最大的问题是必须联网才能工作，如果没有联网就无法实现代码的还原，修改，对比，提交等。

<!--more-->

<div align=center>
  <img src="https://cdn.jsdelivr.net/gh/zzhjoker/hexo-cdn@1.2/git/svn.jpg">
</div>
- SVN 的优点
  1. 采用集中式，易于管理，保证安全性。
  2. 管理方便，逻辑明确，理念符合常规思维。
  3. 代码一致性高。
  4. 适合人数不多的项目开发。
  5. 允许一个文件有任意的可命名属性，会关注所有的文件类型。
  6. 支持二进制文件，更容易处理大文件。
  7. 支持空文件

- 集中式管理缺点
  1. 服务器压力大，数据库容量暴增。
  2. 必须连接在服务器上，否则基本不能工作，提交，对比还原等。
  3. 不适合开源开发。

### Git

> git 是分布式版本控制系统，那么就没有中央服务器，每个人的个人电脑就是一个完整的版本库，搬砖的时候就不需要联网，版本库都在自己的个人电脑上.多人如何协作，只需要把各自的修改推送给对方，就可以互相的看见对方的修改.相比集中式管理分布式管理安全性就会高很多，因为如果一个人的电脑坏了丢失了版本，可以从小组其他人员那里随便复制一个就可以，而集中式版本控制系统的中央服务器要是出了问题那么所有人都无法进行正常的搬砖。

<div align=center>
  <img src="https://cdn.jsdelivr.net/gh/zzhjoker/hexo-cdn@1.2/git/git.png">
</div>

- git 优点
  1. 适合分布式开发，强调个体。
  2. 公共的服务器压力和数量都不会太大。
  3. 速度快，成熟架构，开发灵活。
  4. 任意两个开发者之间可以很容易的解决冲突。
  5. 离线工作，管理代码成本低，不需要依赖服务器。
  6. 部署方便，基本上下个命令就可以用。
  7. 良好的分支机制，可以让主干代码保持干净。
- git 缺点
  1. 代码保密性差。
