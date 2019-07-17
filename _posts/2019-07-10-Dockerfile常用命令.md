---
layout: post
title: Dockerfile常用命令
date: 2019-07-10
tags: Jekyll
---


### 目录

* [dockerfile 命令](#a)

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

WORKDIR
> WORKDIR 用于从镜像创建一个新容器时，在容器内部设置一个工作目录时，ENTRYPOINT和CMD指定的程序会在这个目录中进行。
```
WORKDIR /opt/webapp/db
RUN bundle install
WORKDIR /opt/webapp
ENTRYPOINT ["rackup"]
```

ENV
> ENV指令用来在镜像构建过程中设置环境变量。 和DOCKER RUN命令行的-e标志来传递环境变量的效果一样。


USER
> USER指令用来指定该镜像会以什么样的用户去运行。
```
USER nginx
```

VOLUME
> VOLUME指令用来基于镜像创建的容器添加卷。

ADD
> ADD指令用来将构建环境下的文件和目录复制到镜像中。ADD指令需要源文件位置和目的文件位置两个参数。该命令可以自动压缩和解压。
```shell
ADD software.lic /opt/application/software.lic
```

COPY
> 和ADD指令类似，根本不同在于COPY只关心在构建上下文中复制本地文件，而不会去做文件提取和解压工作。
```
COPY conf.d/ /etc/apatch2
```
第一个路径是本地路径，本地路径必须在DOCKERFILE 文件之下的位置；第二个是容器里面的路径，必须是绝对路径。
如果容器内路径不存在，则会自动创建该路径，如同makir -p 命令那样。

LABEL
> LABEL指令用于为DOCKER镜像中添加元数据，元数据以键值对的形式展现。推荐将所有的元数据都放在一条LABEL指令中，以防止不同的元数据指令创建过多镜像层。可以使用 docker inspect 命令查看容器标签。











