---
title: How to add comment valine
date: 2020-11-23 08:47:16
tags:
  - Blog
  - Hexo
categories:
  - Blog
---

如何在自己blog的每一篇文章后添加评论系统，这里主要讲添加valine的步骤。

<!--more-->

## Step 1
首先，需要注册leancloud用户，该网站有国际版和中文版，中文版需要实名注册，国际版不需要实名注册。
[leancloud国际版](https://leancloud.app/ "leancloud国际版")
[leancloud中文版](https://leancloud.cn/ "leancloud中文版")

## Step 2
创建应用
![leancloud](leancloud1.png "创建应用")
新建两个class（Comment, Counter）
![leancloud](leancloud2.png "新建class")
新建class，要求权限为“无限制”
![leancloud](leancloud3.png "新建class")
“安全中心”/“服务开关”只保留“数据存储”为打开状态
![leancloud](leancloud4.png "数据存储")
获取AppID/AppKey
![leancloud](leancloud5-2.png "AppID/AppKey")

## Step 3
修改next配置文件_config.yml
```python
# Valine
# For more information: https://valine.js.org, https://github.com/xCss/Valine
valine:
  enable: true
  appid: # Your leancloud application appid
  appkey: # Your leancloud application appkey
  notify: false # Mail notifier
  verify: false # Verification code
  placeholder: Just go go # Comment box placeholder
  avatar: mm # Gravatar style
  guest_info: nick,mail,link # Custom comment header
  pageSize: 10 # Pagination size
  language: # Language, available values: en, zh-cn
  visitor: false # Article reading statistic
  comment_count: true # If false, comment count will only be displayed in post page, not in home page
  recordIP: false # Whether to record the commenter IP
  serverURLs: # When the custom domain name is enabled, fill it in here (it will be detected automatically by default, no need to fill in)
  #post_meta_order: 0
```

## Step 4
重新生成，重启服务
测试
![leancloud](valine.png "valine")
完毕
