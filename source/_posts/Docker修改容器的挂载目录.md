---
title: Docker 修改容器的挂载目录
date: 2020-04-14 22:23:41
tags: Docker
categories: 
 - 技术
 - Docker
---

起因是公司开发环境服务器空间被 Mysql 撑爆，于是想换到同一台服务另外一个空间有余的挂载目录上。
1. 停止 Docker 服务：`关键，修改之前必须停止 Docker 服务`
```bash
$ systemctl stop docker.service
```
2. 修改下两个配置文件中的目录位置，然后保存退出
```bash
$ vim /var/lib/docker/containers/${containerId}/config.v2.json

$ vim /var/lib/docker/containers/${containerId}/hostconfig.json
```
3. 启动 Docker 服务
```bash
$ systemctl start docker.service
```
4. 启动 Docker 容器
```bash
$ docker start <containerName/Id>
```
