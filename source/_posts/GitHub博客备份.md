---
title: GitHub博客备份
date: 2021-05-13 09:12:28
tags:
  - Blog
  - 博客
categories:
  - Blog
  - 博客
---

### 安装备份插件

``` bash
npm install hexo-git-backup --save
```

<!--more-->
### 修改配置文件_config.xml
在末尾添加经下代码
``` bash
backup:
  type: git
  theme: hexo-theme-matery
  message: Back up my blog
  repository:
    github: git@github.com:xxx/xxx.github.io.git,backup
```


### 备份到backup分支

``` bash
hexo backup
```

