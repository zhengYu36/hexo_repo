---
title: docker安装minio
date: 2026-06-10 16:00:00
tags: [docker, minio]
---

参考 url：<https://cloud.tencent.com/developer/article/2145598>

这里有些坑，需要注意额。

```bash
docker run -d \
  -p 9042:9000 \
  -p 9043:9001 \
  --name minio1 \
  -v /home/minio/data:/data \
  -e "MINIO_ROOT_USER=AKIAIOSFODNN7EXAMPLE" \
  -e "MINIO_ROOT_PASSWORD=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY" \
  minio/minio:latest server /data --console-address ":9001"
```

> 注：宿主机端口 9042 映射容器 9000（API），9043 映射 9001（控制台）。
