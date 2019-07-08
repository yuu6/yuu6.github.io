---
layout: post
title: kubernetes 集群重启
date: 2019-07-01
tags: kubenetes kubeadm
---


### 目录

* [重启](#reboot)

### <a name="reboot"></a>重启

>```
sudo swapoff -a
systemctl enable kubelet
journalctl -xeu kubelet
```
