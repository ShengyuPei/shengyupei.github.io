---
title: Ubuntu系统开启SSH
date: 2021-05-12 11:22:57
tags:
  - Ubuntu
  - SSH
categories:
  - Ubuntu
---

### 1. 查看是否安装SSH服务
``` bash
dpkg -l | grep ssh
```

<!--more-->
### 2. 安装SSH
``` bash
sudo apt-get install openssh-server
```
### 3. 查看SSH服务状态
``` bash
dpkg -l | grep ssh
```

### 4. 确认是否开启
``` bash
ps -e | grep ssh
```




