---
title: webpack——搭建
categories: Webpack
tags: webpack搭建
thumbnail: https://cdn.jsdelivr.net/gh/zouzenghu/blog-cdn@1.1.3/webpack/image/timg.jpg
---

### 配置 webpack.config.js 文件

```javascript
module.exports = env => require(`./config/webpack.${env}`)
```

<!--more-->

### 配置 package.json 文件

```json
"srcipts":{
  "dev":"webpack-dev-server --env=dev --host 0.0.0.0",
  "prod":"webpack --env=prod"
}
```

**注意：**如果这个时候启动而项目下没有 src 目录，或者 src 下没有 index.js（ 默认将 src 下 index.js 文件当作入口文件）这时用的还是 webpack 的默认配置文件

```javascript
//启动dev时的报错
ERROR in Entry module not found: Error: Can't resolve './src' in 'D:\webCode\webpack-test
//启动prod时报错
ERROR in Entry module not found: Error: Can't resolve './src' in 'D:\webCode\webpack-test
//报的错一摸一样，提示我们没有找到入口文件
```

### 配置 webpack.dev.js（开发文件）

```javascript
const path = require('path')
//引入merge，功能和Object.assing()一样合并两个对象
const merge = require('webpack-merge')
//引入公共文件
const common = require('./webpack.common')
module.exports = merge(common, {
  //配置成开发模式
  mode: 'development',
  //配置webpack-dev-server
  devServer: {
    //启动服务器时自动打开浏览器
    open: true,
    //指定端口
    port: 8080,
    //开启热更新
    hot: true,
    //启动压缩
    compress: true,
    //指定主页面地址，一般指定dist打包生成目录
    contentBase: path.join(process.cwd(), 'dist')
  }
})
```

### 配置 webpack.common.js （公共文件）

```javascript
const path = require('path')
//打包处理html文件
const HtmlWebpackPlugin = require('html-webpack-plugin')
module.exports = {
  //入口文件配置，如果有多个入口文件则写为对对象
  entry: {
    main: path.join(process.cwd(), 'src/index.js')
  },
  //出口文件配置，[name]占位符勿要将出口文件写死
  output: {
    filename: './js/[name].js',
    //所有的文件将打包在dist目录下，绝对路径
    path: path.join(process.cwd(), 'dist')
  },
  plugins: [
    new HtmlWebpackPlugin({
      //打包名称
      filename: 'index.html',
      //模板地址
      template: path.join(process.cwd(), 'src/index.html'),
      //注入js
      chunks: ['main']
    })
  ]
}
```

### 配置 webpack.prod.js （生产文件）

```javascript
const merge = require('webpack-merge')
const common = require('./webpack.common')
//每次生成前清除一次dist目录
const { CleanWebpackPlugin } = require('clean-webpack-plugin')
module.exports = merge(common, {
  //改为生产模式或none，否则报警高烦
  mode: 'production',
  plugins: [new CleanWebpackPlugin()]
})
```
