---
title:  Ubuntu 开放端口
date: 2022-10-9
tags:
- 环境配置
- Ubuntu
categories:
- [环境配置]
---

### 防火墙相关命令
1. 查看防火墙状态,也可以看到开放的端口
```shell
sudo ufw status
```
2. 关闭防火墙 
```shell
sudo ufw disable
```
3. 打开防火墙
```shell
sudo ufw enable
```
4. 开放端口
```shell
sudo ufw allow 端口号
```
6. 关闭端口
```shell
7. sudo ufw deny 端口号
```
8. 重启防火墙
```shell
sudo ufw reload
```

### 端口开启无法依然无法访问
1. 查看开启的端口是否有程序监听
```shell
netstat -ap | grep 端口
```
3. 如果端口有程序监听，排查程序是否需要配置远程访问（例如redis、mysql都需要配置远程访问）
