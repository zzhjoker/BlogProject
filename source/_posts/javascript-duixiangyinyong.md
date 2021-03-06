---
title: 不可变的原始值和可变的对象引用
categories: JavaScript
toc: true
thumbnail: https://cdn.jsdelivr.net/gh/zzhjoker/hexo-cdn@1.0/javascript/101c1aaf13caf21d5eedb918f6be2f25.jpg
tags:
  - 不可变的原始值和可变的对象引用
---

> javascript 中的原始类型（Undefined，Null，Boolean）与对象类型有着根本的区别，原始类型值是不可更改的，任何方法都无法更改，而对象类型是可变的值是可修改的。

<!--more-->

```javascript
//原始类型
{
  let s = 'Hello World'
  s.tolowerCase()
  console.log(s) // => Hello World
}

//对象类型
{
  let obj = { x: 15 }
  obj.x = 10
  obj.y = 5
}
```

### 值之间的比较

> 原始类型比较的是保存在栈中的值，而对象类型比较的是地址值，而不是实际值的本身。

```javascript
{
  let s = 'Hello World'
  s === 'Hello World'
  //true
}

{
  let obj = {
    name: '李磊'
  }
  let obj2 = {
    name: '李磊'
  }
  obj === obj2
  //false
}
```

### 值之间的赋值

> 对象类型在赋值时，复制的是指针地址而并非对象本身值，所以他们同时引用着同一个对象体，而原始类型赋值时是将自身作为一个副本 copy 一份或者新创建一份给要赋值的变量。

```javascript
{
  let n1 = 5
  let n2 = n1
  n1++
  console.log(n2) //5
}
{
  let obj1 = { n1: 5 }
  let obj2 = obj1
  obj1.n1++
  console.log(obj2.n1)
  // 6
  obj2.n2 = 10
  console.log(obj1.n2)
  // 10
}
```

### 值之间的存储

> 对象类型栈中保存的是指针地址，实际值保存在堆中，原始类型值保存在栈中。

### 对象类型值的复制

> 因为对象类型是引用类型，将对象赋值给另一个变量，仅仅是赋值的引用值，对象本身并没有赋值一次，所以如果想得到一个对象或者数组的副本，则必须显式的复制对象的每个属性或数组中的每个元素。

```javascript
let obj1 = {
  name: '李磊',
  money: '1000万'
}
let obj2 = {}
for (let key in obj1) {
  obj2[key] = obj1[key]
}
```
