---
title:  CentOS7配置IP地址
date: 2021-09-18
tags:
- 环境配置
- Centos7
- Vmware
categories:
- [环境配置]
---
#### 1. 获取网卡名称
```shell
ip addr
```
![图片消失了!](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305171659621.png)

>
>ens33 为网卡名（根据实际的情况，看你显示的是什么）
>

#### 2. 进入 /etc/sysconfig/network-scripts 查看网卡配置文件
```
cd /etc/sysconfig/network-scripts
```
#### 3. 输入**ls**获取文件列表，查看文件
```
ls
```
![图片消失了!](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305171718578.png)

>**一般为ifcfg-enoxxxxxx**
>xxxx 一般为一串数字
>

#### 4. 准备修改配置文件
```
vi ifcfg-enoxxxxxx
```
> ifcfg-enoxxxxxx 输入你虚拟机中真实的文件名
> 

#### 5. 开始修改配置文件
##### 1. 修改部分
bootproto=static
onboot=yes

##### 2. 添加部分
```
IPADDR=192.168.52.131
NETMASK=255.255.255.0
GATEWAY=192.168.52.2
DNS1=8.8.8.8
DNS2=8.8.8.4
```
>IP地址 IPADDR
> IPADDR=192.168.网段.地址
>> 网段是子网IP设置的网段
>>> 网段
>>> ![图片消失了!](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305171852208.png)
>>> 

>> 地址可以填100 - 240 的值，不和其他虚拟机的IP地址重复即可
>> 

>子网掩码 NETMASK 
>一般 255.255.255.0 就可以了
>

> 网关 GATEWAY
> 看你虚拟机的网关配置是什么
>> ![图片消失了!](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305171904654.png)
>> ![图片消失了!](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305171905791.png)
>> 设置成一样的即可

> NDS服务器 NDS1和DN2
> 可以设置为
>> DNS1=8.8.8.8
>> DNS2=8.8.8.4

#### 6. 配置完成如图：
![图片消失了!](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305171728193.png)

> 理解后操作
