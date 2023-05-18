---
title:  wampserver橙色解决方法汇总
date: 2021-09-20
tags:
- 环境配置
categories:
- [环境配置]
---
## 原因1(大多数情况由此造成)：IIS及SQL服务冲突
### 1. **关闭IIS服务**
    1.1  快捷键  Win+R 输入  `compmgmt.msc` （打开计算机管理）
    默认这个是关闭的
    ![](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305161809249.png)
      	1.2 让IIS停止
    ![](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305161810421.png)
### 2. **关闭SQL Server Reporting Service和MYSQL服务**
快捷键 Win+R 输入`services.msc`（打开服务）
找到SQL Server Reporting Service及MYSOL服务，停止服务
![](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305161814587.png)
**修改后，重启WAMPserver，显示为绿色，进入浏览器，地址栏输入：localhost ，成功进入即成功**

## 原因2：Apache没能开启
( 1为绿色，2为灰色 ) 异常情况
![](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305161817538.png)
>该图为正常情况

### 问题(1)：端口被占用
#### 解决方法[1]：查看占用端口的进程，关闭该进程

#### 解决方法[2]：修改端口
1.1 找到  **httpd.conf**  打开
![](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305161822422.png)

1.2 **Ctrl+F查找  `Listen`**
![](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305161825600.png)
1.3 修改冒号后的数字端口为目标端口，两处一同修改
### 问题(2)：由于系统的某项应用运行的Apache，导致wampserver的Apache的就被占用了
一般与IIS服务有关，一般是IIS的Apache启动了，把它关掉