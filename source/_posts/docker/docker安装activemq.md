---
title: docker安装activemq
date: 2026-06-10 16:00:00
tags: [docker, activemq]
---

这个主要是关于消息中心的技术框架验证

参考 url: <https://developer.aliyun.com/article/572390>

设置密码: <https://blog.csdn.net/yan_lang/article/details/128790125> — 测试 ok 了，也启动成功了

参考 url: <https://blog.csdn.net/qq_37880968/article/details/106895991>

这个不需要利用 docker 来进行安装，直接下载即可。

可以执行下面的命令即可，这个就是对上面的更好的封装（这个好像没有生效）：

```bash
docker run -d --name activemq -p 61616:61616 -p 8161:8161 -e AMQ_USER=admin -e AMQ_PASSWORD=adminnwh webcenter/activemq
```

浏览器输入 <http://127.0.0.1:8161/>，点击 Manage ActiveMQ broker，使用默认账号/密码：`admin/admin` 进入查看。
