---
title: typescript class
categories: Typescript
toc: true
thumbnail: https://cdn.jsdelivr.net/gh/zzhjoker/hexo-cdn@1.0/typescript/typescript.jpg
tags:
  - typescript——类
---

Typescript 中定义类

```javascript
class Greeter {
  greeting: string
  construction(message: string) {
    this.greeting = message
  }
  greet() {
    return 'Hello,' + this.greeting
  }
}
let greeter = new Greeter('Typescript')
greeter.greet()
```

<!--more-->

### 继承类

Typescript 中类的继承

```javascript
class Animal {
  distance: string
  constructor(distance: string) {
    this.distance = distance
  }
  move() {
    console.log(`Animal moved ${this.distance}`)
  }
}
class dogs extends Animal {
  constructor(distance: string) {
    super(distance)
  }
  blok() {}
}
const dog: {} = new dogs('Typescript')
```

### 类的修饰符

1. public 公共修饰符 默认

```javascript
//默认是public公共
class Animal {
  public distance: string
  public constructor(distance: string) {
    this.distance = distance
  }
  public move() {
    console.log(`Animal moved ${this.distance}`)
  }
}
const dog: {} = new Animal('Typescript')
```

2. private 私有修饰符，在对象外无法访问，只可在对象或者实例中使用

```javascript
class Animal {
  //只可以自己访问，外部或派生继承皆无法访问
  private distance: string
  public constructor(distance: string) {
    this.distance = distance
  }
  private move() {
    console.log(`Animal moved ${this.distance}`)
  }
}
class dogs extends Animal {
  constructor(distance: string) {
    super(distance)
    //报错无法在派生实例中访问
    //this.distance
  }
  blok() {}
}
//报错无法在外部访问
//const dog: {} = new Animal('Typescript').move()
```

3. protected 受保护的属性，只能自己访问或者在派生类中访问，外部无法访问

```javascript
class Animal {
  protected distance: string
  protected constructor(distance: string) {
    this.distance = distance
  }
  move() {
    console.log(`Animal moved ${this.distance}`)
  }
}
class dogs extends Animal {
  constructor(distance: string) {
    super(distance)
  }
  blok() {}
}
const dog: {} = new dogs('Typescript')
//报错，受保护无法在外部访问
//console.log(dog.distance)
//报错，受保护无法在外部访问
//new Animal('Typescript')
```

4. readonly 修饰符，只读修饰符仅创建时可修改或者使用 as 修改

```javascript
class Animal {
  readonly distance: string
  protected constructor(distance: string) {
    this.distance = distance
  }
  move() {
    console.log(`Animal moved ${this.distance}`)
  }
}
class Animal {
  readonly distance: string
  constructor(distance: string) {
    this.distance = distance
  }
  move() {
    console.log(`Animal moved ${this.distance}`)
  }
}
//报错无法修改
//let a: {} = (new Animal('Typescript').distance = '2')
```
