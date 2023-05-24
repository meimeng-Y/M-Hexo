---
title:  Docker配置远程访问
date: 2023-5-20
tags:
- Docker
categories:
- []
---
# Docker配置远程访问
## 最简单的方法（不安全）
### 1.修改文件
```sh
# vim /usr/lib/systemd/system/docker.service
# 在13行
ExecStart=/usr/bin/dockerd -H fd:// \
    -H tcp://0.0.0.0:2375 \ #添加
    --containerd=/run/containerd/containerd.sock

```
### 2. 重载配置
```sh
systemctl daemon-reload
```
### 3.重启docker服务
```sh
systemctl restart docker 
```
