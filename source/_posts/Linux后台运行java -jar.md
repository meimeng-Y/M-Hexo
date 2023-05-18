---
title:  Linux后台运行java -jar
date: 2022-09-3
tags:
- 小问题
- java
- jar
categories:
- [小问题]
---

# Linux后台运行java -jar
## 问题描述
打好的jar包，放在服务器上之后，在windows里面用xshell打开一个连接，然后运行java -jar xxx 执行这个jar文件，关闭这个链接时程序停止运行

## 解决方法
### 方法一：后台启动程序(不推荐)
```sh
java -jar XXX.jar &
```
>当前窗口不被锁定，输出的日志会显示在屏幕上，当关闭窗口的时候，不会停止执行。 

### 方法二：nohup 不挂断运行的命令(推荐)
> nohup 不挂断运行的命令，当终端或者账户关闭的时候，程序依旧运行。
> 当前的命令默认会把日志输出到nohup.out文件中 
> 
```shell
nohup java -jar XXX.jar &
```
>指定输出文件 
>可以指定路径

```shell
nohup java -jar XXX.jar >log.out &
```
>查看后台启动命令 
>显示后台运行的程序。每个作业前面都有一个作业的编号。 
```shell
jobs
```

>调回前台控制
>

```shell
fg + 编号
```



