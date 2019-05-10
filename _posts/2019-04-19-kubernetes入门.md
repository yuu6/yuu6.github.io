---
layout: post
title: kubernetes入门
date: 2019-04-19
tags: k8s
---


* [k8s设计理念？](#k8s-design)
* [k8s的网络？](#k8s-network)
* [什么是pod？](#What-is-pod)
* [什么是service？](#What-is-service)
* [什么是deployment？](#What-is-deployment)
* [什么是scheduler？](#What-is-scheduler)
* [什么是kube-dns？](#What-is-kube-dns)
* [什么是kube-proxy？](#What-is-kube-proxy)
* [什么是kubernetes-api-server？](#What-is-kubernetes-api-server)


### <a name="What-is-k8s"></a>什么是K8S？

### <a name="k8s"></a>K8S架构

<div align="center">
	<img src="/images/posts/k8s/k8s1.png" height="300" width="300">  
</div>

### <a name="k8s-design"></a>K8S设计理念

+ API设计原则

+ 控制机设计原则

### <a name="k8s-network"></a>K8S的网络

### <a name="What-is-pod"></a>什么是pod？

### <a name="What-is-service"></a>什么是service？

> + 负载均衡

### <a name="What-is-deployment"></a>什么是deployment？

### <a name="What-is-scheduler"></a>什么是scheduler？

+ 优选规则

+ 预选规则



### <a name="What-is-kube-dns"></a>什么是kube-dns？

### <a name="What-is-kube-proxy"></a>什么是kube-proxy？

可以设置安全的访问机制，比如设置白名单


### <a name="What-is-kubernetes-api-server"></a>什么是kubernetes-api-server？
kubernetes api server 最主要的REST接口是资源对象的增删改查，除此之外，他还提供了一类很特殊的REST接口-kubernetesproxyapi接口。
