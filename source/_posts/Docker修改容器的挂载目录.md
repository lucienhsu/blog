---
title: Docker 修改容器的挂载目录
date: 2020-04-14 22:23:41
tags: Docker
---

起因是公司开发环境服务器空间被 Mysql 数据库撑爆，于是想换到同一台服务另外一个空间有余的挂载目录上。
1. 停止docker服务：关键，修改之前必须停止docker服务
```
systemctl stop docker.service
```
2. 修改下买呢配置文件中的目录位置，然后保存退出
```
vim /var/lib/docker/containers/${containerId}/config.v2.json
```
```
vim /var/lib/docker/containers/${containerId}/hostconfig.json
```
3. 启动docker服务
```
systemctl start docker.service
```
4. 启动docker容器
```
docker start <containerName/Id>
```
