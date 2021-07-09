---
title: Ubuntu重启后无关连接向日葵
date: 2021-05-17 14:52:04
tags:
  - Ubuntu
categories:
  - Ubuntu
---

Ubuntu系统，在系统登录后，远程通过向日葵可以直接访问，但是重启后，需要人工再进行系统登录。

<!--more-->

### 解决办法

``` bash
sudo vi /etc/profile.d/xrk.sh
输入：
#!/bin/bash
xhost+
```
保存退出，改写访问权限即可。

``` bash
chmod 777 xrk.sh
```
