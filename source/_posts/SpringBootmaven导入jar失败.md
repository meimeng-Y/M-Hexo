---
title:  SpringBoot Maven导入jar失败
date: 2022-10-20
tags:
- SpringBoot
- java
- jar
categories:
- [SpringBoot]
---

# SpringBoot Maven导入jar失败
## 报错信息
```sh
Could not transfer artifact org.springframework.boot:spring-boot-starter-parent:pom:
```
## 用maven执行强制更新命令
```sh
clean install -e -U
```
## 镜像源ssl有问题
>
>在settings—maven中按照以下设置
>目的：配置完可忽略安全校验
>

```sh
-Dmaven.wagon.http.ssl.insecure=true 
-Dmaven.wagon.http.ssl.allowall=true
```
