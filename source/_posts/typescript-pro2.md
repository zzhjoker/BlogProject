---
title: typescript 类接口定义
categories: Typescript
toc: true
thumbnail: https://cdn.jsdelivr.net/gh/zouzenghu/blog-cdn@1.1.2/typescript/image/foreground_bluprint.svg
tags:
  - typescript——类接口定义
---

类的公共成员描述

```javascript
interface Clock {
  currentTime: Date;
}
class Clock implements Clock {
  currentTime: Date
  construction(h: number, m: number) {}
}
```

<!--more-->

### 类接口定义

既检查实例也检查公共属性

```javascript
//定义实例接口
interface ClockInterface {
  //检测实例，实例原型接口
  tick(): void;
}
//定义静态接口
interface ClockConstructor {
  //实例签名
  new(hour: number, minute: number): ClockInterface;
}
//使用接口
function craeteClock(
  ctor: ClockConstructor,
  hour: number,
  minute: number
): ClockInterface {
  return new ctor(hour, minute)
}
//定义类
class DigitalClock implements ClockInterface {
  constructor(h: number, m: number) {}
  tick() {
    console.log('cick toc')
  }
}
//使用实例
let digital = craeteClock(DigitalClock, 12, 17)
console.log(digital)
```

### 继承接口

Typescript 中接口也是可以继承的，将一个接口复制到另一个接口

```javascript
interface Shape {
  color: string;
}
interface PenStroke {
  penWidth: number;
}
//继承多个接口
interface Square extends Shape, PenStroke {
  sideLength: number;
}
let squre= {} as Square;
squre.color = 'red'
squre.sideLength = 10
squre.penWidth =2
```

### 混合类型

当我们希望描述一个既是函数又是对象的类型时，可以使用混合类型

```javascript
interface Counter {
  //函数类型定义
  (start: number): string
  //对象属性定义
  interval:number
  //对象方法定义
  reset():void
}
//使用混合类型
function getCouter(): Counter {
  let counter = function(start: number) {} as Counter
  counter.interval = 23
  counter.reset = function() {}
  return counter
}
```
