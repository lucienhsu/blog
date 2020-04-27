---
title: Mac下解决v2端口被占用，shadowsocket(ss)程序残留问题
date: 2020-04-27 09:40:20
toc: true
tags: MacOs
categories: 
 - 技术
 - MacOs
---

# 起因
更新系统后，每次重启电脑打开 V2ray，都提示：`listen tcp 127.0.0.1:1087: bind: address already in use`

# 解决
1. 检查占用端口的进程
```bash
$ lsof -i tcp:1087
# 输出
COMMAND  PID   USER   FD   TYPE             DEVICE SIZE/OFF NODE NAME
privoxy 1475 lucien    3u  IPv4 0x5f67c8aa941ec26f      0t0  TCP localhost:cplscrambler-in (LISTEN)

```

2. 根据 PID 获取进程的主程序名称
```bash
$ launchctl list
# 输出
PID	Status	Label
6606	-9	com.qiuyuzhou.shadowsocksX-NG.http

```
发现原来是 ss 会在后台自动运行；
接下来就简单了，两个方法：删除 ss 或者 打开 ss 然后退出；
