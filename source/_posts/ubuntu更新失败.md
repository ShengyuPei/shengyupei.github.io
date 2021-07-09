---
title: ubuntu更新失败
date: 2021-05-17 14:45:30
tags:
  - Ubuntu
categories:
  - Ubuntu
---

## 报错
``` bash
sudo apt-get update
E: 仓库 “http://ppa.launchpad.net/fcitx-team/nightly/ubuntu bionic Release” 没有 Release 文件。
```
<!--more-->

### 方法1

``` bash
sudo vi /etc/apt/sources.list
```
使用以上命令删除无法使用的源

### 方法2
所有程序->"软件和更新"->"其它软件"
选中无法使用的源，点击"删除"即可。

