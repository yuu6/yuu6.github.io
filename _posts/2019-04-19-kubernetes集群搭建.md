---
layout: post
title: kubernetes集群搭建
date: 2019-04-19
tags: k8s
---

* [环境介绍？](#env_intro)
* [关闭防火墙](#step1)
* [安装集群？](#step2)
* [解决故障](#step3)


### <a name="env_intro"></a>环境介绍？

首先应该搭建多台虚拟机，并且记录好每台的信息，分配好主从节点。

|主机名|ip|型号|
:----:|:----:|:-----:
|master|192.168.206.XXX|centos7.6|
|slave1|192.168.206.XXX|centos7.6|
|slave2|192.168.206.XXX|centos7.6|


### <a name="step1"></a>关闭防火墙

查看防火墙状态

```
firewall-cmd --state
```

停止firewall


```
systemctl stop firewalld.service
```

禁止firewall开机启动

```
systemctl disable firewalld.service 
```

关闭selinux 

进入到/etc/selinux/config文件

```
vi /etc/selinux/config
```

将SELINUX=enforcing改为SELINUX=disabled

### <a name="step2"></a>安装集群

[集群安装步骤](https://blog.51cto.com/2168836/2106963)


### <a name="step3"></a>解决故障

[解决故障](https://blog.csdn.net/qq_38695182/article/details/82971114)