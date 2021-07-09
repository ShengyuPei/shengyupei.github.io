---
title: RPP
date: 2020-05-02 19:46:07
tags:
  - Person ReID
categories:
  - Person ReID
---

# RPP网络模型
[Beyond Part Models: Person Retrieval with Refined Part Pooling (and a Strong Convolutional Baseline)](https://arxiv.org/abs/1711.09349 "下载")

<!--more-->
![RPP](RPP1.png "RPP")

![RPP](RPP2.png "RPP")

RPP网络模型的实施步骤如下：
![RPP](RPP3.png "RPP")

RPP网络结构跟PCB的是一样的，RPP是PCB的升级版。PCB使用partical思想，将其硬水平分割为6部件。RPP在PCB的基础上，也是分割为6部件，但并不是硬分割，而是软分割。
RPP这里使用了类似于注意力机制的方法，将这6部件分配给一个可以学习的参数。
