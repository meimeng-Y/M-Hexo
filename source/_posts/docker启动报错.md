---
title:  docker启动报错
date: 2021-10-20
tags:
- 环境配置
- Centos7
- docker
categories:
- [环境配置]
---

# docker启动报错
## 重启docker报错信息
>重启docker报错信息
>

```sh
Job for docker.service failed because the control process exited with error code. See “systemctl status docker.service” and “journalctl -xe” for details.
```
>启动docker报错信息
>

```sh
Job for docker.service failed because start of the service was attempted too often. See “systemctl status docker.service” and “journalctl -xe” for details.
To force a start use “systemctl reset-failed docker.service” followed by “systemctl start docker.service” again.
```
## 问题产生原因
> daemon文件后缀格式造成重启/启动失败
 
## 解决方案
### 1.进入docker目录下：
```shell
cd /etc/docker
```
### 2.修改daemon文件后缀：
```shell
mv daemon.json daemon.conf
```
### 3.重启/启动docker：
```shell
systemctl start docker
```
