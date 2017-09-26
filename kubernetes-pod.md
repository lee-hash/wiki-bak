---
layout: post
title: Kubernetes Pod
date: 2017-07-08 11:10:00
tags:
- docker
categories: Java
description: docker
banner: http://ohaq3i4w3.bkt.clouddn.com/docker-01.png
---

# Pod

> A Pod is a group of one or more application containers (such as Docker or rkt) and includes shared storage (volumes), IP address and information about how to run them.



# Pods overview
![Pod](https://d33wubrfki0l68.cloudfront.net/fe03f68d8ede9815184852ca2a4fd30325e5d15a/98064/docs/tutorials/kubernetes-basics/public/images/module_03_pods.svg)


# Pod特性
1. 每个Pod包含一个或多个container
2. 每个Node可以有一个或多个Pod
3. 一个Kubernetes集群中，每个Pod有一个唯一的IP地址，甚至相同Node上的不同Pod


# Reference
[kubernetes-interactive-tutorials/kubernetes-basics/explore-intro/](https://kubernetes.io/docs/tutorials/kubernetes-basics/explore-intro/)