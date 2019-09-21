---
title: ES6——Set
categories: ES6
toc: true
thumbnail: https://cdn.jsdelivr.net/gh/zouzenghu/blog-cdn@1.1.2/typescript/image/foreground_bluprint.svg
tags:
  - ES6——Set
---

### Set 数据结构

> **ES6** 中提供了新的数据结构`set`，`set` 类似于数组，但是不同的是成员的值都是唯一的，没有重复，set 本身是一个构造函数用来生成 set 数据结构

- 声明 set 数据结构

```javascript
//使用new关键字创建一个Set结构
let set = new Set()

//set函数可以接受一个数组进行初始化
let set = new Set([1, 2, 3, 2, 1, 2, 3, 2])

//set函数也可以接受一个类数组对象进行初始化
let set = new Set(document.querySelectorAll('div'))
```

#### 操作方法

- add(value)

```javascript
//添加某个值，返回set结构本身
```

- delete(value)

```javascript
//删除某个值，返回一个布尔值表示是否成功
```

- has(value)

```javascript
//返回一个布尔值表示该参数，是否是该set的成员
```

- clear()

```javascript
//清空整个set结构
```

遍历方法
