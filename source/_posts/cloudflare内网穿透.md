---
title: cloudflare内网穿透
date: 2023-05-7
tags:
- 随身WIFI
categories:
- [随身WIFI]
---
#### 1.下载程序


```shell
wget https://git.histb.com/cloudflare/cloudflared/releases/download/2023.5.0/cloudflared-linux-arm -O /usr/bin/cloudflared
```
`https://git.histb.com/cloudflare/cloudflared/releases`
2023.5.0 去官方找最新的版本号 [cloudflared仓库](https://git.histb.com/cloudflare/cloudflared/releases) 

#### 2.设置权限

```shell
chmod +x /usr/bin/cloudflared
```
#### 3.登录
```shell
cloudflared login
```
#### 4.把ssh页面的网址复制到浏览器打开 登录，然后授权域名

#### 5.创建隧道
```shell
cloudflared tunnel create *** # ***是隧道名
```
#### 6.把上一步的隧道ID复制下来粘贴到下面的两个位置
```
tunnel: 隧道ID

credentials-file: /root/.cloudflared/隧道ID.json

ingress:

  - hostname: 要穿透的域名，不能一级域名

    service: http://127.0.0.1

  - service: http_status:404
```
以上内容用vim config.yml放到配置文件
```
vim config.yml
```
#### 7.新建配置文件的存放文件夹
```
mkdir -p /etc/cloudflared/
```
#### 8.把配置文件移动到该文件夹内
```
cp config.yml /etc/cloudflared/
```
#### 9.给隧道分配域名
```
cloudflared tunnel route dns 隧道名 域名
```
#### 10.安装服务
```
cloudflared service install
```
#### 11.设置自启动
```
systemctl start cloudflared
```
#### 12.查看信息
```
systemctl status cloudflared
```
#### 删除的命令
```
cloudflared service uninstall
 rm -rf /root/.cloudflared/cert.pem
```

