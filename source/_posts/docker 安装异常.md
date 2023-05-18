---
title:  docker 安装异常
date: 2022-10-26
tags:
- 小问题
- docker
categories:
- [小问题]
---
# docker 安装异常
## 异常信息

```shell
 inotify_add_watch(7, /dev/dm-4, 10) failed: No such file or directory
```


## 原因
> xfsprogs 版本太低了


## 解决方法
>安装 xfsprogs
```shell
yum update xfsprogs
```

