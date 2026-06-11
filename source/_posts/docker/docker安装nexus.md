---
title: docker安装nexus
date: 2026-06-10 16:00:00
tags: [docker, nexus]
---

```bash
docker pull sonatype/nexus:pro-2.15.2
```

> ps：这个有的时候官方镜像可以拉取，有的时候又不可行，看来跟网络环境有关系。

```bash
mkdir /opt/nexus-data && chown -R 200 /opt/nexus-data

docker run -d -p 8081:8081 --name nexus \
  -v /opt/nexus-data:/sonatype-work \
  sonatype/nexus:pro-2.15.2
```

> ps：注意上面这个版本需要认证码，没有去折腾这个，所以还是用的以前的 nexus 来实现的。以前的私库是没有外部挂载的，是通过镜像包获取的方式哈。

意思是挂载？

```bash
docker run -d -p 8081:8081 --name nexus nexus3.3/centos:7
```

## 访问地址

<http://192.168.229.36:8081> — 注意这个是没有挂载外包的，数据都是在容器里面的。

## 默认密码

```
admin/admin123
```

后续推送成功，同时拉取也是成功的，后面这些代码就可以参考这个。

但是这两个其实在 AI 时代的作用不大了，因为 AI 可以很轻易的实现相同的功能，所以这个就叫做降维打击：

1. 代码混淆
2. 上传源码
