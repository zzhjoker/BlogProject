---
title: Event Loop
categories: JavaScript
toc: true
thumbnail: https://cdn.jsdelivr.net/gh/zouzenghu/blog-cdn@1.1.2/typescript/image/foreground_bluprint.svg
tags:
  - Event Loop
---

### 单线程含义

> 浏览器是 multi-process，一个浏览器只有一个 Browser Process，负责管理 Tabs，协调其他 process 和 Renderer Process 存至 memory 内的 Bitmap 绘制到页面上；在 Chrome 中，一个 Tab 对应一个 `Render Process`，Render process 是 `multi-thread`，其中 `main thread` 负责渲染（GUI render engine）执行 JS（JS engine）和 event loop；network component 可以开 2~6 个 I/O threads 平行去处理

### Event Loop
