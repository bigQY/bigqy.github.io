---
title: "使用wsl安装图形界面版kali"
date: 2021-09-07T20:15:30+08:00
draft: true
slug: "kali-in-wsl2-with-desktop"
image: "https://api.paugram.com/wallpaper"
categories:
    - linux
tags:
    - kali
    - WSL
description: "使用wsl2安装kali，并且开启图形界面"
---

## 打开wsl功能
你可以使用powershell或者图形界面打开wsl功能

1. 使用powershell(管理员)输入以下命令

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

2. 使用图形界面打开wsl，搜索`启用或关闭windows功能`  
![](post/kali-in-wsl2-with-desktop/193811.png)
打开`适用于 Linux 的 Windows 子系统`，保存并重启
![](post/kali-in-wsl2-with-desktop/194127.png)


## 升级WSl2

目前只有wsl2才支持图形界面，所以你需要升级你的wsl到wsl2，如果你已经是wsl2的话可以跳过这个步骤  
首先，在[这个链接](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)下载wsl内核升级包  
等待下载完成，安装重启(可能不需要重启，推荐还是重启一下)  
将wsl默认版本改为2  
```powershell
wsl --set-default-version 2
```
## 从 Microsoft Store 安装 kali 
直接在windows自带的市场里安装kali linux就行  
安装完成之后会提示你设置账号密码，按需设置
## apt换源
由于安装图形界面需要下载不少东西，默认的apt源可能比较慢，这里我们换成阿里源   
```shell
sudo nano /etc/apt/sources.list #这里的nano可以换成其他的编辑器，看你喜好
```
将官方源的url替换成https://mirrors.aliyun.com/kali，其他的部分不要改  
## 安装图形界面
输入命令  
```shell
sudo apt update
sudo apt install -y kali-win-kex
```
这个过程大概需要下载2G的内容，等待一会即可下载安装完成  
## 如何使用图形界面
安装完毕之后，就能使用图形界面了  
kali-win-kex一共有三种模式，我这里只介绍两种常用模式
1. Window Mode  
启动方式  
```shell
kex --win -s
```
启动之后会直接创建一个全屏窗口来显示kali图形界面  
退出kali需要点击右上角的log out  

2. Enhanced Session Mode
启动方式  
```shell
kex --esm --ip -s
```
启动之后会使用RDP进行连接，可以非全屏调整窗口大小  

启动的过程中可能会有一些 防火墙请求，建议允许，否则会影响一些功能，比如声音。
