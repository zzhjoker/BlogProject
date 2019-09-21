---
title: npm install 后报错
categories: buglog
toc: true
thumbnail: https://cdn.jsdelivr.net/gh/zouzenghu/blog-cdn@1.1.4/errorBlog/timg.jfif
tags:
  - 错误日志-npm
---

引起错误的原因，当我想安装一个 `npm` 包时但是却一直安装失败报错提示我某个 `.git` 文件错误，目前具体引起问题的原因不明

### 错判日志

```javascript
//错误命令
npm install npm i zzhjoker-randomweight

//错误日志
npm ERR! path D:\webCode\webapck\node_modules\zzhjoker-randomweight
npm ERR! code EISGIT
npm ERR! git D:\webCode\webapck\node_modules\zzhjoker-randomweight: Appears to be a git repo or submodule.npm ERR! git     D:\webCode\webapck\node_modules\zzhjoker-randomweight
npm ERR! git Refusing to remove it. Update manually,
npm ERR! git or move it out of the way first.

npm ERR! A complete log of this run can be found in:
npm ERR!     C:\Users\17600\AppData\Roaming\npm-cache\_logs\2019-08-17T06_27_30_818Z-debug.log
```

### 解决方法

使用命令`rm -rf node_modules/*/.git/`，如果 rm 无效或者是无效命令或者参数，删除 node_modules 重新 npm install
