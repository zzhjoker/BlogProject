---
title: typescript 类存取器 & 抽象类
categories: Typescript
toc: true
thumbnail: https://cdn.jsdelivr.net/gh/zouzenghu/blog-cdn@1.1.2/typescript/image/foreground_bluprint.svg
tags:
  - typescript——类存取器
---

如果当一个对象属性发生改变时我们想让其发生一些事件，这个时候存取器就排上用场

```javascript
class Employee {
  //私有属性用来实际存储age值
  private _age: number = 0
  //获取age属性时自动触发
  get age(): number {
    console.log(this._age)
    return this._age
  }
  //设置age属性时自动触发
  set age(newAge: number) {
    if (newAge > 18 && newAge < 45) {
      this._age = newAge
    } else {
      alert('年龄必须符合在大于18且小于45')
    }
  }
}
```

### 抽象类

```javascript
```
