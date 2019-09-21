---
title: npm安装全局包后无法识别自定义指令
categories: buglog
toc: true
thumbnail: https://cdn.jsdelivr.net/gh/zouzenghu/blog-cdn@1.1.4/errorBlog/timg.jfif
tags:
  - 错误日志-npm
---

### 情况记录

npm 安装的全局 `npm` 包，npm 包自带指令在控制台死活无法识别，报错不是函数或者错误指令

### 错误原因

npm 全局包路径未在环境变量中挂载

### 解决方法

使用 `npm prefix -g` 命令挂载到环境变量中，关闭 vscode，重启 vscode 即可
C:\Users\17600\AppData\Roaming\npm
