---
title: 使用clean-webpack-plugin打包时报错
categories: buglog
toc: true
thumbnail: https://cdn.jsdelivr.net/gh/zouzenghu/blog-cdn@1.1.4/errorBlog/timg.jfif
tags:
  - 错误日志-webpack
---

### 情况说明

今日在配置 `webpack` 项目模板时，配置到 `clean-webpack-plugin` 时，总是重复稳定的复现一个错误，错三次，大概的情况是 `clean-webpack-plugin` 在未取得 `admin` 电脑管理权的电脑上运行会受限，删除文件时需要管理员权限

### 错误详情

```javascript
//大概意思是不允许删除某个文件或者没有权限删除某个文件
Error: EPERM: operation not permitted, lstat 'D:\reactnative\MyBaby\node_modules
.staging\react-native-vector-icons-2612cf43\Fonts\Zocial.ttf'
```

### 解决方法

将当前 `windowns` 用户转到 `admin` 管理员群组下或者切换到管理员账户才可以解决 `clean-webpack-plugin` 没有权限的错误，至于怎么取得权限这个可以百度百科一下
