---
title: axios——接口定义
categories: Vue
thumbnail: https://cdn.jsdelivr.net/gh/zouzenghu/blog-cdn@1.1.2/typescript/image/foreground_bluprint.svg
tags: 重构vue-axios
---

使用 typescript 重构 vue-axios

<!--more-->

### 定义参数接口，约定参数格式

```javascript
//types -> index.ts
//所有公共类型定义文件
//定义约定字面量，如果要使用method传入字符串必须是一下规定内容
export type Methods =
  | 'get'
  | 'GET'
  | 'delete'
  | 'Delete'
  | 'head'
  | 'HEAD'
  | 'options'
  | 'OPTIONS'
  | 'post'
  | 'POST'
  | 'put'
  | 'PUT'
  | 'patch'
  | 'PATCH'
//定义参数对象接口
export interface AxiosRequestConfig {
  url: string
  //使用字面量约定方式
  method?: Methods
  data?: any
  params?: any
}

```

### 定义 axios 方法

```javascript
//参数对象接口定义文件
import { AxiosRequestConfig } from './types/index'
//请求方法
import xhr from './comonpoents/xhr'
//将params转为url格式字符串
import { buildURL } from './comonpoents/helpers/url'
//使用types中定义的接口类型，指定为AxiosRequestConfig
//定义axios方法
function axios(config: AxiosRequestConfig): void {
  //先将config.url进行处理
  processConfig(config)
  //在交给xhr发送给服务器
  xhr(config)
}
function processConfig(config: AxiosRequestConfig): void {
  //将url交给transformURL进行转换
  config.url = transformURL(config)
}
function transformURL(config: AxiosRequestConfig): string {
  const { url, params } = config
  //使用buildURL进行处理并返回
  return buildURL(url, params)
}
export default axios
```

### 处理 url

```javascript
import { isDate, isObject } from './util'
function encode(val: string): string {
  return encodeURIComponent(val)
    .replace(/%40/g, '@')
    .replace(/%3A/gi, ':')
    .replace(/%24/g, '$')
    .replace(/%2C/gi, ',')
    .replace(/%20/gi, '+')
    .replace(/%2B/gi, '[')
    .replace(/%2D/gi, ']')
}
//参数类型声明url string类型  params任意类型可有可无  返回值string类型
export function buildURL(url: string, params?: any): string {
  //判断如果params为空则直接返回url即可
  if (!params) {
    return url
  }
  const parts: string[] = []
  Object.keys(params).forEach(key => {
    console.log(params[key])
    const val = params[key]
    //判断如果val是空则跳出本次循环
    if (val === undefined || `${val}` === 'null') {
      debugger
      console.log(val)

      //跳出本次循环
      return
    }
    //声明values值为任意数组，用于保存值为数组的值
    let values: any = []
    if (Array.isArray(val)) {
      //判断val是否是数组，如果是数组则将值直接赋值给values
      values = val
      key += '[]'
    } else {
      //否则则将val转为数组并赋值为values
      values = [val]
    }

    values.forEach((vals: any) => {
      if (isDate(vals)) {
        vals = vals.toISOString()
      } else if (isObject(val)) {
        vals = JSON.stringify(val)
      }
      parts.push(`${encode(key)}=${encode(vals)}`)
    })
  })
  let seriglizedParms = parts.join('&')
  if (seriglizedParms) {
    const markIndex = url.indexOf('#')
    if (markIndex !== -1) {
      url = url.slice(0, markIndex)
    }
    url += (url.indexOf('?') === -1 ? '?' : '&') + seriglizedParms
  }
  return url
}
```
