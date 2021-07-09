---
title: Ubuntu系统挂载NTFS磁盘
date: 2021-05-24 08:34:42
tags:
  - Ubuntu
  - NTFS
categories:
  - Ubuntu
---

### 卸载其他磁盘
``` bash
sudo umount -a
```

<!--more-->

安装ntfs-3g
``` bash
sudo apt install ntfs-3g
```

查看挂载情况
``` bash
sudo fdisk -l
```

挂载指定磁盘
``` bash
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -ro force
```

修改系统文件，开机自动挂载
``` bash
sudo vi /etc/fstab
```

添加挂载对象
``` bash
UUID="" /media/sdb1 ntfs-3g defaults,locale=zh_CN.UTF-8,gid=1000,uid=1000,umask=002 0   0
```

