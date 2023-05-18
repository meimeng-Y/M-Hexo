---
title:  git取消对某个文件的跟踪
date: 2022-10-21
tags:
- Git
categories:
- [Git]
---

> 文件被**commit**过后将它忽略
> 文件被**commit**过后你再建立 **.gitignore**文件将它忽略是无效的
> 需要使用命令将它忽略

#### 删除文件的跟踪，并保留在本地。
```sh
git rm --cached 
```
> git rm --cached xxxx 删除xxxx的跟踪，并保留在本地。
> 

#### 删除目录的跟踪，并保留在本地。
```sh
git rm -r --cached
```
> git rm -r --cached xx  删除xx目录，并保留在本地。
> 

#### 删除文件的跟踪，不保留在本地。
```sh
git rm --f
```
>git rm --f xxxx 删除xxxx的跟踪，并且删除本地文件。
