---
layout: post
title: kubernetes 集群重启
date: 2019-07-01
tags: kubenetes kubeadm
---


### 目录

* [重启](#reboot)

### <a name="reboot"></a>重启
使用kubeadm搭建集群时，有时候服务器重启之后集群并没有启动，这时需要执行下面的命令来重启集群。
```
sudo swapoff -a
systemctl enable kubelet
journalctl -xeu kubelet
```
