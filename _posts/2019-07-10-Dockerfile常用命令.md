---
layout: post
title: Dockerfile常用命令
date: 2019-07-10
tags: Jekyll
---


### 目录

* [dockerfile 命令]](#a)

### <a name="a"></a>Dockerfile命令

CMD
> 用于在docker启动时执行命令；要运行的命令要存放在数组里；如果指定了多条CMD命令，也只执行最后一条；DOCKER RUN命令可以覆盖CMD命令；

```shell
CMD ["/bin/bash", "-l"]
```

ENTRYPOINT
> ENTRYPOINT指令提供的命令不容易在容器启动时被覆盖，实际上，DOCKER RUN 命令行中指定的任何参数都会被当成参数再次传递给ENTRYPOINT指令中指定的命令。
```shell
# 同时使用CMD 和 ENTRYPOINT命令
ENTRYPOINT ["/usr/sbin/nginx"]
CMD ["-h"]
```





