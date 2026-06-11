---
title: docker安装达梦数据库
date: 2026-06-10 16:00:00
tags: [docker, 达梦数据库, dm8]
---

## 1. 拉取镜像文件

参考 url：<https://hub.docker.com/r/xuxuclassmate/dameng>（这个地址是可以拉取的）

```bash
docker pull xuxuclassmate/dameng
```

## 2. 运行

```bash
docker run -d -p 5236:5236 --restart=always --name dameng --privileged=true \
  -e PAGE_SIZE=16 \
  -e LD_LIBRARY_PATH=/opt/dmdbms/bin \
  -e INSTANCE_NAME=dm8db \
  xuxuclassmate/dameng
```

## 3. 进入容器

```bash
docker exec -it dameng bash
```

## 4. 登录达梦数据库

```bash
./opt/dmdbms/bin/disql SYSDBA/SYSDBA001
```

- 默认账号：**SYSDBA**
- 默认密码：**SYSDBA001**

## 5. 如何连接数据库

<https://www.cnblogs.com/miracle-luna/p/17665761.html>（这个是可以连接的）

## 6. 设置大小写不敏感（重要）

参考：<https://blog.csdn.net/Januea/article/details/134240787>

```bash
docker run -d -p 5236:5236 \
  --restart=always \
  --name dm8 \
  --privileged=true \
  -e CASE_SENSITIVE=0 \
  -e UNICODE_FLAG=1 \
  -e CHARSET=1 \
  -e PAGE_SIZE=16 \
  -e LD_LIBRARY_PATH=/opt/dmdbms/bin \
  -e INSTANCE_NAME=dm8 \
  -v /opt/data/dm8_test:/opt/dmdbms/data \
  xuxuclassmate/dameng
```
