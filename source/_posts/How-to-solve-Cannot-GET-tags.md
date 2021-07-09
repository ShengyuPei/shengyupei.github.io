---
title: How to solve Cannot GET /tags/
date: 2020-11-20 09:06:27
tags:
  - GitHub
  - Blog
  - Hexo
categories:
  - Blog
---

从GitHub下载的Hexo theme Next，当在首页使用tags和categories时，会发现Cannot GET /tags/，Cannot GET /categories/。
打开public/categories，public/tags，可以看到里面有内容，但没有生成index.html文件。这就是导致问题的原因。当然index.html应该是自动生成的，就像public/archives下也生成了index.html一样。那到底应该如何解决呢？查看了网上的教程，记录一下方法：
<!--more-->
# 教程
## Step 1
首先需要生成新页面
```shell
hexo new page categories
hexo new page tags
```
## Step 2
在source下生成了categories和tags两个文件夹，编辑categories/index.md，加上
```python
type: categories
```
同理，编辑tags/index.md，加上
```python
type: tags
```

## Step 3

重新生成，重启服务
```shell
hexo g
hexo server
```
完毕！

