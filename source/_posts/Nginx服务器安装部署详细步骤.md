---
title: Nginx服务器安装部署详细步骤
date: 2022-09-2
tags:
- Nginx
categories:
- [环境配置]
---
### 安装环境：
Linux服务器操作系统：CentOs 8.1.1911

Nginx版本：1.16.1（Linux）

### 安装步骤：
#### **1. 安装GCC、automake、pcre、zlib和openssl **

可以通过如下指令去查看Linux服务器上是否已经安装pcre、zlib和openssl
```shell
//查看openssl
rpm -qa openssl
//查看zlib
rpm -qa zlib
//查看pcre
rpm -qa pcre
```
安装了以上三个第三方库，所以显示版本。

如果没有安装以上三个库，鉴于以上Nginx运行的需求，我们需要执行以下代码：
`yum -y install gcc gcc-c++ automake pcre pcre-devel zlib zlib-devel openssl openssl-devel`

#### **2.下载Nginx服务器并解压**
下载Nginx服务器本文提供了两种方式：
A、通过官网进行下载，进入Nginx官网，网址：http://nginx.org/en/doload.html 本文Nginx版本为1.16.1，可以选择对应的版本进行下载。
B、通过Linux进行下载，指令代码：

``` shell
wget http://nginx.org/download/nginx-1.16.1.tar.gz
```
本文通过第二种方式进行下载。
```
//进入opt文件夹
cd /opt

//创建Nginx文件夹
mkdir Nginx

//下载Nginx服务器文件
wget http://nginx.org/download/nginx-1.16.1.tar.gz

//解压文件
tar -xvf nginx-1.16.1.tar.gz
```
解压完成后/opt/Nginx文件夹下多出一个文件夹Nginx-1.16.1，该文件夹下包含如下文件：

auto：存放了大量脚本文件，和configure脚本程序有关。

conf：存放了Nginx服务器的配置文件，包含了Nginx服务器的基本配置文件和对部分特性的配置文件。

configure：Nginx服务器的自动脚本程序，运行configure自动脚本将会完成两项工作：
> 1. 检查环境，根据环境检查结果生成C代码；
> 
> 2. 生成编译代码需要的makefile文件。

html：存放了两个后缀名为.html的静态文件。

man：存放了Nginx服务器的帮助文档，可通过 man nginx进行查看。

src：存放了Nginx服务器的所有源代码。

#### **3.安装Nginx服务器**
**（注意：此步骤在运行.configure时可能不成功，不成功的原因基本在于pcre、zlib或openssl未安装成功，可以重新进行安装）**
```shell
// opt/Nginx文件夹下创建新文件夹Nginx-1.16.1_install
cd /opt/Nginx
mkdir Nginx-1.16.1_install
 
//进入之前解压后得到的文件夹nginx-1.16.1
cd nginx-1.16.1
 
//运行configure脚本程序，可以直接运行./configure,也可以通过--prefix=path 指定nginx的安装目录
./configure --prefix=/opt/Nginx/Nginx-1.16.1_install
 
//运行完成后,该文件夹下多出一个文件---Makefile，此时执行make指令进行源代码编译，编译过程中屏幕会有编译全过程
make
 
//编译完成后，执行make的install命令安装Nginx服务器
make install
```
执行完成**make install**指令后，可以将工作目录定位到我们的安装目录，也就是上述的**/opt/Nginx/Nginx-1.16.1_install**文件夹，通过**ls -l**指令，可以看到该文件夹下出现以下几个文件夹：
![](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305161916958.png)
conf：该目录存放了Nginx的所有配置文件，该文件夹下包含nginx.conf文件，它是Nginx服务器的住配置文件，其他文件则是用    来配置Nginx的相关功能。

html：该目录存放了Nginx服务器在运行过程中调用的一些html文件。

logs：该目录存放了Nginx服务器的日志。

sbin：该目录中只包含了一个文件-nginx，它就是Nginx服务器的主程序。

#### **4.修改nginx.conf文件** 
```
// 修改nginx.conf文件中端口，如修改成81
cd /opt/Nginx/Nginx-1.16.1_install/conf
vim nginx.conf
```
修改完成后如下图所示：
![](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305161924951.png)

#### **5、启动Nginx服务器**

```shell
//在启动服务器之前，我们可以通过如下指令来查看Nginx服务器配置文件是否有语法错误：
//绝对路径
/opt/Nginx/Nginx-1.16.1_install/sbin/nginx -t

//在Nginx-1.16.1_install文件夹中时的相对路径
./sbin/nginx -t

//通过如下指令可以查看Nginx服务器版本
./sbin/nginx -v

//使用默认配置启动Nginx
./sbin/nginx

//查看Nginx进程状态
ps -ef|grep nginx

//停止Nginx服务器
//绝对路径
/opt/Nginx/Nginx-1.16.1_install/sbin/nginx -s stop

//Nginx-1.16.1_install文件夹下相对路径
./sbin/nginx -s stop

//重启Nginx服务器
/opt/Nginx/Nginx-1.16.1_install/sbin/nginx -s reopen

//重新载入配置文件
/opt/Nginx/Nginx-1.16.1_install/sbin/nginx -s reload
```

#### **6、访问服务器地址**
ip地址+端口

![示例图](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305161928147.png)
