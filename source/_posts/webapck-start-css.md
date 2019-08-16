---
title: webpack——静态文件处理
categories: Webpack
tags: webpack——静态文件处理
thumbnail: https://cdn.jsdelivr.net/gh/zouzenghu/blog-cdn@1.1.3/webpack/image/timg.jpg
---

webpack 默认只能处理 js 文件其余任何文件都无法处理，所以我们必须配置单独的 loader 或者 plugin 来处理对应的文件

<!--more-->

### 处理 css 文件

需要的开发依赖

```javascript
//css文件处理loader
npm install css-loader -D
//sass文件处理loader
npm install sass-loader -D
//处理sass文件
npm install node-sass -D
//预处理css语法前缀
npm install postcss-loader -D
//预处理css语法前缀插件
npm install autoprefixer -D
//自动将css文件插入到html文档中
npm install mini-css-extract-plugin -D

```

需要创建的文件

```javascript
new-item postcss.config.js
//postcss.config.js
//自动添加浏览器兼容前缀依赖
module.exports = {
  plugins: [
    new require('autoprefixer')
  ]
}
```

```javascript
module: {
  rules: [
    {
      //css处理
      test: /\.(sa|sc|c)ss$/,
      use: [
        {
          loader: miniCssExtractPlugin.loader,
          options: {
            //解决css中引入图片位置错误问题（根据打包路径决定）
            publicPath: '../'
          }
        },
        {
          loader: 'css-loader',
          options: {
            //必须走下面两个loader才能上来
            importLoaders: 2
          }
        },
        'sass-loader',
        'postcss-loader'
      ]
    }
  ]
}
```

### 处理 image 文件

### 处理字体文件
