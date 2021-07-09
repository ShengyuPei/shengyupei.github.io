---
title: Add local search to Next theme
date: 2020-11-20 10:42:05
tags:
  - Blog
  - Hexo
categories:
  - Blog
---

如何在hexo next theme下添加search功能呢，这里先讲local search功能的添加。
<!--more-->

## Step 1
安装插件，首先切换到hexo目录下，
```shell
npm install hexo-generator-search --save
npm install hexo-generator-searchdb --save
```
如果出现error，可以先执行
```shell
npm init -y
```
在hexo目录下生成文件package.json，再执行上述语句。
## Step 2
编辑hexo/_config.yml文件，添加代码
```python
# search
search:
  path: ./public/search.xml
  field: post
  format: html
  limit: 10000	# 表示限制搜索文字
```
## Step 3
编辑hexo/themes/next/_config.yml文件，修改代码
```python
local_search:
  enable: true
  # If auto, trigger search by changing input.
  # If manual, trigger search by pressing enter key or search button.
  trigger: auto
  # Show top n results per article, show all results by setting to -1
  top_n_per_article: 1
  # Unescape html strings to the readable one.
  unescape: false
  # Preload the search data when the page loads.
  preload: false
```
## Step 4
重新生成，重新启动服务
```shell
hexo clean #这个有时也是必须的，清除掉缓存，上传GitHub后才会没毛病。
hexo g
hexo d     #上传GitHub
hexo server

```
完毕！

