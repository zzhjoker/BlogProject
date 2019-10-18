---
title: 包装类型对象
categories: JavaScript
toc: true
thumbnail: https://cdn.jsdelivr.net/gh/zouzenghu/blog-cdn@1.1.2/typescript/image/foreground_bluprint.svg
tags:
  - 包装类型对象
---

> JavaScript 对象是一种复合值，它是属性或者方法的集合，通过`.属性名/方法名`的方式来引用属性值或者方法。当我们试图操作字符串数字时，为什么这些基础类型或者原始类型会给我们提供方法或者属性。

<!--more-->

```javascript
{
  let s = 'Hello World'
  s.substring(1)
  //"ello World"
}
```

> 基础类型为什么会具备方法或者属性，实际上当我们试图操作字符串基础类型值时，JavaScript 引擎都会自动调用`new String(s)`的方式将原本的基础类型 s 转换成对象，这个对象则继承 String 的属性和方法，并被用来处理属性的引用，一旦属性引用结束，这个新创建的对象就会自动的被销毁。所以这个对象只存在引用的一瞬间，之后随即被销毁。Number 类型和 RegExp 类型亦是如此。

```javascript
{
  let s = 'Hello World'
  //自动调用new String()对象包装字符串
  s = new String(s).substring(1)
  //销毁
  s = null
  //实际实现上并不一定是创建或者销毁，但是整个过程则看起来像是这样
}
```
