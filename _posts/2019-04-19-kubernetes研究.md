---
layout: post
title: kubernetes研究
date: 2019-04-19
tags: k8s
---


## 介绍



### 目录

* [安装docker](#install-docker)
* [构建自己的docker镜像](#build-myself-image)
* [运行docker](#run-docker)



### <a name="install-docker"></a>安装dicker?

+ [安装docker](https://www.jianshu.com/p/00e162bf587a)

+ 登陆

```shell
docker login
```

> 在docker官网申请id

+ 运行测试脚本

``` shell
docker run busybox echo "Hello World"
```

+ docker 运行

```
docker run <image>:<tag>
```

### <a name="build-myself-image"></a>构建自己的docker镜像?

+ 创建自己的应用

+ 创建Dockerfile文件

+ 构建容器镜像

```
docker build -t kubia .
```
