---
title: typescript interface
categories:
  - Typescript
toc: true
thumbnail: https://cdn.jsdelivr.net/gh/zouzenghu/blog-cdn@1.1.2/typescript/image/foreground_bluprint.svg
tags:
  - typescript接口定义
---

TypeScript 的核心原则之一是对值所具有的结构进行类型检查。它会检查我们的值是否跟类型所匹配,它有时被称做“鸭式辨型法”或“结构性子类型化”。 在 TypeScript 里，接口的作用就是为这些类型命名和为你的代码或第三方代码定义契约。

```javascript
//关键字 interface
//定义接口规则
interface LbelledValue {
  label: string;
}
//使用接口
function printLabel(labelledObj: LbelledValue) {
  console.log(LbelledValue.label)
}
//参数传递必须按照接口规则
printLabel({
  label: 'Hello Typescript'
})
//当接口定义后使用接口的对象则不可在随意的添加属性
```

<!--more-->

### 可选属性

**注意：** 如果未定义可选属性，那么接口规则中的属性都是必选属性

```javascript
//关键字 ？
//定义参数规则
interface user {
  name: string //必选属性
  age: number
  sex?: string //可选属性
}
//定义返回值规则
interface result {
  name: string
  age: number
  sex: string
}
//使用定义的接口规则
function createUser(user: user): result {
  if (user.age > 70 && user.age < 18) {
    user.age = 0
  }
  user.sex = user.sex || '否'
  return {
    //返回值必须和接口定义的规则相同
    name: user.name,
    age: user.age,
    sex: user.sex
  }
}
console.log(createUser({ name: '张三', age: 1 }))
```

### 只读属性

当有些特殊对象属性在只有创建时才可以修改，而其他任何时候只能读取不可修改时，就要使用只读属性来定义。

```javascript
//关键字 readonly
interface Point{
  readonly x: number
  readonly y: number
}
//定义值后，属性值不可在改变
let p1 :Point = {x:10 , y:20}
//报错
//p1.x = 10

```

### 只读数组

区分 cosnt 和 readonly，当我们是对变量进行定义的话使用 const 如果是对属性进行定义的话使用 readonly

```javascript
//只读数组
//数组定义后只可创建时修改，甚至
let list: ReadonlyArray<number> = [1, 2, 3, 1]
//报错
// list.push(2)
// list[1] = 2
// let arr=list
// arr.push(2)

//如果想修改可以使用断言语句强行修改
//将list断言为正常语句在赋值给arr
let arr = list as number[]
arr.push(8)
```

### 额外属性检查

typescript 会对对象字面量的方式进行额外的检查，一旦发现传递的对象某些属性不在接口定义中 typescript 就会报错

```javascript
//使用对象字面来量的方式进行传递参数
interface user {
  name: string
  age: number
  sex?: string
}
function createUser(user: user): void {
  if (user.age > 70 && user.age < 18) {
    user.age = 0
  }
  user.sex = user.sex || '否'
  console.log(`姓名${user.name} 年龄${user.age} 性别${user.sex}`)
}
//typescript会进行额外的检查
createUser({ name: '张三', age: 1 })
//报错
//createUser({ name: '张三', age: 1,home:'浙江省绍兴市' })
```

```javascript
//使用非对象字面量方式进行参数传递
//不会进行额外的检查
let users = {
  name: '张三',
  age: 1,
  home: '浙江省绍兴市'
}

createUser(users)
```

### 额外属性

当我们确定，除了必要的属性或许会多出额外属性时，可以使用**[属性名:索引类型]:值类型**的方式定义额外属性

```javascript
interface user {
  name: string
  age: number
  sex?: string
  //定义额外属性，索引签名为string类型值为任意类型
  [extra: string]: any
}
function createUser(user: user): void {
  if (user.age > 70 && user.age < 18) {
    user.age = 0
  }
  user.sex = user.sex || '否'
  console.log(`姓名${user.name} 年龄${user.age} 性别${user.sex}`)
}
createUser(
    {
    name: '张三',
    age: 18,
    sex:'男',
    home:'浙江省绍兴市'
    }
)
```

### 函数类型

typescript 中接口不仅可以描述普通的对象属性，而且还可以描述函数类型

```javascript
//定义函数接口声明
interface SearchFun {
  (source: string, subString: string): boolean;
}
//使用接口定义
let mySearch: SearchFun
//定义函数
mySearch = function(src, sub) {
  let result = src.search(sub)
  return result > -1
}
```

在使用完函数接口定义后，定义函数时参数不必与接口定义的索引一致，而且参数列表中也不必声明类型，只需让 typescript 自动进行类型推断即可，但是唯一保证的是，值类型和返回值类型以及参数个数一致否则会报错

### 可索引类型

typescript 对一个索引类型进行描述

```javascript
//定义索引类型描述
interface StringArray {
  //定义索引签名，定义值类型
  [index: number]: string;
}
//使用
let myArray: StringArray
myArray = ['Tom', 'lilei']
let name: string = myArray[0]
```
