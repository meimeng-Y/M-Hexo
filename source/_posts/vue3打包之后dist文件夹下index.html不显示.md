---
title:  vue3打包之后dist文件夹下index.html不显示
date: 2022-09-24
tags:
- 小问题
- 前端
- vue3
categories:
- [小问题]
---
# vue3打包之后dist文件夹下index.html不显示
**没有配置文件**
>没有了配置文件，默认公共路径是'/'
>所以需要自己创建配置文件去更改路径
>配置文件只能在项目的根目录下创建（跟src文件平级）
>并且文件的名字只能是 **vue.config.js**
>添加
```vue
module.exports = {
    publicPath: './'
}
```

**添加后会出现路由跳转问题**
在router文件夹下的index.js里这样改
```js
import { createRouter, createWebHistory } from 'vue-router'

const router = createRouter({
  //改这个方法createWebHashHistory(是hash模式)
  history: createWebHashHistory(),//而createWebHistory()方法则为history模式
  routes
})
```
