---
layout: post
title: kubernetes集群安全机制
date: 2019-04-26
tags: k8s
---
* [k8s认证](#k8s-authentication)
* [k8s授权](#k8s-authorization)
* [k8s准入控制](#k8s-admission-control)

* [HTTPS证书认证](#https)
* [HTTP Token认证](#http-token)
* [HTTP Base认证](#http-base)


### <a name="k8s-authentication"></a>k8s认证
> HTTPS
```
openssl genrsa -out ca.key 2048             //genrsa生成rsa私钥
openssl req -x509 -new -nodes -key ca.key -subj "/CN=kube-master" -days 5000 -out ca.crt //生成x509证书

openssl genrsa -out server.key 2048
```
> HTTP Token
> HTTP Base

### <a name="k8s-authorization"></a>k8s授权
> AlwaysDeny
> AlwaysAllow
> ABAC

### <a name="k8s-admission-control"></a>k8s准入控制
> 
