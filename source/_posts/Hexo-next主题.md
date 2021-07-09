---
title: Hexo next主题
date: 2020-11-19 15:25:59
tags: 
  - Hexo
  - GitHub
  - Blog
categories:
  - Blog
---

[hexo theme next (GitHub)](https://github.com/theme-next/hexo-theme-next "hexo next")
```shell
$ cd hexo
$ git clone https://github.com/theme-next/hexo-theme-next themes/next
```
修改hexo/_config.yml
```python
# theme: landscape
theme: next
```
需要重新启动hexo server
```shell
hexo g
hexo server
```
<!--more-->
# Tricks
## 修改hexo/theme/next/_config.yml
```python
# Schemes
#scheme: Muse
#scheme: Mist
scheme: Pisces
#scheme: Gemini
```
## 修改首页显示文章数目
```python
index_generator:
  path: ''
  per_page: 5
  order_by: -date
```

## 在文章相应部分前加语句，首页显示不会很长
```python
<!--more-->
```



