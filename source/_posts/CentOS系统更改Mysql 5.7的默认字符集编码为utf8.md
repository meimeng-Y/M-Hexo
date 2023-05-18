---
title:  CentOS 6/7系统更改Mysql 5.7的默认字符集编码为utf8
date: 2022-09-15
tags:
-  CentOS
categories:
- [环境配置]
---

# CentOS 6/7系统更改Mysql 5.7的默认字符集编码为utf8

## 查看当前字符集编码
进入MySql，执行命令
```sql
show variables like '%char%';
```
![](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305172242872.png)

可以看到目前一部分默认的字符集编码为**latin1**。

## 修改字符集为utf8
### 1. 备份mysql配置文件my.cnf
```sh
cp /etc/my.cnf /etc/my.cnf.bak
```
> 防止改坏了
> 
![](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305172245102.png)

### 2. 修改文件
```sh
 vim /etc/my.cnf
```
 > vim没安装，用vi命令
 > 

```
character-set-server=utf8		//新增配置项
datadir=/var/lib/mysql
socket=/var/lib/mysql/mysql.sock
symbolic-links=0
log-error=/var/log/mysqld.log
pid-file=/var/run/mysqld/mysqld.pid

[client]                		//新增配置项
default-character-set=utf8		//新增配置项

[mysql]                     	//新增配置项
default-character-set=utf8		//新增配置项
```
修改后的文件
![](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305172248465.png)

### 3. 重启mysql服务
```sh 
service mysqld restart 
```
> mysqld是你安装是的服务名，默认应该是mysqld
> 

### 4.查看修改后的字符集编码
进入MySql，执行命令
```sql
show variables like '%char%';
```
![](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305172253790.png)
完成