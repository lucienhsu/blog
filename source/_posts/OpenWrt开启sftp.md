---
title: OpenWrt 开启 sftp
date: 2020-04-14 23:04:57
tags: OpenWrt
categories: 
 - 技术
 - OpenWrt
---
执行一下指令：
```bash
$ opkg update

$ opkg install vsftpd openssh-sftp-server

$ /etc/init.d/vsftpd enable

$ /etc/init.d/vsftpd start
```
