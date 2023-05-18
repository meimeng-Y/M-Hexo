---
title:  Git如何永久删除文件(包括历史记录，保留更新历史)
date: 2022-10-24
tags:
- Git
categories:
- [Git]
---

# Git如何永久删除文件(包括历史记录，保留更新历史)
## 前言
在使用git的时候不小心把远程的数据库密码推送到gitee的公开仓库，而且推送过几次更新，需要将该配置文件删除，并删除历史记录的推送

## 步骤一: 清除文件
打开项目的Git Bash,使用命令: 
``` shell
git filter-branch --force --index-filter 'git rm --cached --ignore-unmatch xxxxxxxx ' --prune-empty --tag-name-filter cat -- --all
```
>其中 xxxxxxxx  就是你要删除的文件的相对路径(要在项目路径下打开Git Bash)
>
>**<u>注意一点，这里的文件或文件夹，都不能以 '/' 开头，否则文件或文件夹会被认为是从 git 的安装目录开始</u>**
>
>>如果删除的是文件夹
>
>> 在 
>
>> ```shell
>> git rm --cached
>> ```
>
>>  命令后面添加
>> ```shell
>> -r
>> ```
>> 命令，表示递归的删除

注意:  如果以后也不会再上传这个文件或文件夹, 把这个文件或文件夹添加到.gitignore文件里, 然后再push你的repo.

## 步骤二: 推送我们修改后的repo
以**强制覆盖**的方式推送你的repo, 命令如下:
```
git push origin master --force --all
```
这个过程其实是重新上传我们的repo, 比较耗时, 虽然跟删掉重新建一个repo有些类似, 但是好处是<u>**保留了原有的更新记录**</u>
