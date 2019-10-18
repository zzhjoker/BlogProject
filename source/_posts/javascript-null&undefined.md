---
title: null & undefined
categories: JavaScript
toc: true
thumbnail: https://cdn.jsdelivr.net/gh/zouzenghu/blog-cdn@1.1.2/typescript/image/foreground_bluprint.svg
tags:
  - null & undefined
---

> `null` 和 `undefined` 是 javascript 中的关键字，它们常用来描述一个特殊值“空值”。犀牛书上解释**undefined 是表示系统级的，出乎意料的或类似错误的值的空缺，而 null 是表示程序级的，正常的或在意料之中的值的空缺**

<!--more-->

```javascript
typeof null
// "object"

typeof undefined
// "undefined"

null == undefined
//true

null === undefined
//false

Number(null)
//0

Number(undefined)
//NaN

if (null) {
  //默认转换为false
}
if (undefined) {
  //默认转换为false
}
```

### Null

> Null 类型，代表一个空对象的指针，使用 typeof 运算得到`"Object"`，所以可以理解为 null 是一个特殊的对象值。

### Undefined

> Undefined 类型当变量声明后但未赋值，默认初始化值为 undefined。

### 总结

> undefined 是访问一个未初始化的变量时返回的值，而 null 是访问一个尚未存在的对象时返回的值，可以将 undefined 看做空的变量，而 null 则看做空的对象。在定义一个变量想保存一个对象时，可以暂时先将值赋值为 null，这样可以体现 null 是一个空指针对象，也更好的区分 null 和 undefined。虽然本质上两者表示的都是空值。
