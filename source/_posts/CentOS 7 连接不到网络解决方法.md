---
title:  CentOS7查看开放端口命令及开放端口号
date: 2021-09-18
tags:
- 环境配置
- Centos7
- Vmware
categories:
- [环境配置]
---
### 配置环境
使用VM16创建虚拟机并安装CentOS 7，但是安装完成后发现连接不到网络。
网络连接模式为NAT
![图片消失了!](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305171628646.png)
### 解决方案
这里给出NAT模式下对应的的解决方法：
#### 1. 注意子网地址，和掩码
>
>如果在虚拟机设置了静态IP,要保证子网地址和虚拟机设置了静态IP的网段要一样
>一般不一样的情况是：从其他的设备拷贝了虚拟机，或者是重置了网卡
>

![图片消失了!](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305171630773.png)

#### 2. 要保证虚拟机里面的IP要一致，这样才能连通（设置了静态IP要注意）
![图片消失了!](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305171637212.png)

#### 3. 打开任务管理器，保证这三个服务处于运行状态。开启后，关闭虚拟机重启Vmware。
![图片消失了!](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305171644642.png)
