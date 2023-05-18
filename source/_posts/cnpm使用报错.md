---
title:  cnpm使用报错
date: 2022-09-3
tags:
- npm
- javascript
categories:
- [环境配置]
---

# cnpm使用报错
## 问题
**cnpm使用报错throw err;^Error: Cannot find module 'fs/promises**
![](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305172258415.png)
## 问题定位

**node 版本过高**

## 解决方案：
1. 查看你的cnpm的版本是不是高于8.2.0
```sh
cnpm -v
```
2. 查看node版本
```sh
node -v
```
>  cnpm 8.2.0 版本及以上，无法在 12.16.1 的node 版本下使用
>  

可以**升级node**或者**降低cnpm版本**
**降低cnpm版本方案**
首先卸载 cnpm
```sh 
npm uninstall -g cnpm
```
安装指定版本 cnpm
```sh 
npm install cnpm@7.1.0 -g
```
