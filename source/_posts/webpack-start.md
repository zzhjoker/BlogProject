---
title: webpack
categories: Webpack
tags: 初识webpack
thumbnail: https://cdn.jsdelivr.net/gh/zouzenghu/blog-cdn@1.1.3/webpack/image/timg.jpg
---

- 什么是 webpack
  webpack 的作用是将复杂的项目分割，打包，合并，降级，来维护项目
  本质上，webpack 是一个现代 JavaScript 应用程序的静态模块打包器当
  webpack 处理应用程序时，它会递归地构建一个依赖关系图，其中包含应
  用程序需要的每个模块，然后将所有这些模块打包一个或多个 bundle，它
  可以将浏览器不识别的最新语法降级为 ES5 或者更低的语法，webpack 的定
  意就是模块打包器，将各个模块进行打包，而其他附加的功能，如语法降级
  sass 编译，等都是在打包的过程中进行的
  <!--more-->

### npm 命令

```javascript
npm install module -D ///将指定的包安装到当前的项目目录下 -g(全局)
npm uninstall name // 将指定的包删除
npm install //自动安装项目中所需要的依赖包
```

### webpack 起步安装

```javascript
//初始化为一个npm项目
 npm init -y
 //安装webpack到本地项目中 -D 安装在开发依赖包上dependencies
 npm install webpack -D
 //安装wepback脚手架工具
 npm install webpack-cli -D
 //运行项目
 npx webpack 入口文件
 //如果未指定webpack.config文件，那么将使用webpack默认自带的配置文件
```

### webpack 基本包

![基本开发依赖](https://cdn.jsdelivr.net/gh/zouzenghu/blog-cdn@1.1.3/webpack/image/2019-08-14_214150.png)

```javascript
//处理开发环境文件与生产环境文件
npm install webpack-merge -D
//打包html模板，默认只能处理js文件
npm install html-webpack-plugin -D
//webpack服务器
npm install webpack-dev-server -D
```

### 创建基本目录

![基本目录](https://cdn.jsdelivr.net/gh/zouzenghu/blog-cdn@1.1.3/webpack/image/2019-08-14_212818.png)

```javascript
//创建webpack控制文件目录
mkdir config
//创建源码目录
mkdir src
```

### 创建基本文件

```javascript
//创建webpack控制文件将默认文件覆盖
new-item webpack.config.js
cd config
//webpack公共文件
new-item webpack.common.js
//webpack开发文件
new-item webpack.dev.js
//webpack生产文件
new-item webpack.prod.js
```

## 全局安装与项目安装 webpack

- 全局安装

```javascript
npm install webpack -g
npm install webpack-cli -g

```

- 项目安装

```javascript
cd 项目目录
npm install webpack -D
npm install webpack-cli -D
npm install webpack@版本号 -D 指定版本安装 webpack

```

- webpack 命令

```javascript
npm webpack Path 这是使用全局的 webpack
npx webpack Path 这是使用当前项目中的 webpack
npx webpack -v 查看当前使用的 webpack 版本
npx webpack --config filename 使用指定的 webpack 配置文件
```
