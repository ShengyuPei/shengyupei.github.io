---
title: Ubuntu环境下搭建hexo-github博客
date: 2020-04-30 18:32:29
tags: 
  - Hexo
  - GitHub
  - Blog
categories:
  - Blog
---
# 一、安装 Node.js和npm
```shell
sudo apt-get update
sudo apt-get install nodejs
sudo apt-get install npm
```
适时更新一下，查看nodejs和npm版本号
```shell
nodejs -v
npm -v
```
<!--more-->
# 二、安装 Hexo
创建目录，并安装
```shell
mkdir hexo
cd hexo
sudo npm install -g hexo-cli
hexo init
```
继续安装
```shell
sudo npm config set user 0
sudo npm config set unsafe-perm true
sudo npm install -g hexo-cli
```

接着安装相关插件

```shell
npm install hexo-generator-index --save
npm install hexo-generator-archive --save
npm install hexo-generator-category --save
npm install hexo-generator-tag --save
npm install hexo-server --save
npm install hexo-deployer-git --save
npm install hexo-deployer-heroku --save
npm install hexo-deployer-rsync --save
npm install hexo-deployer-openshift --save
npm install hexo-renderer-marked --save
npm install hexo-renderer-stylus --save
npm install hexo-generator-feed --save
npm install hexo-generator-sitemap --save
```

重启系统，测试是否安装成功？

```shell
hexo server
```
提示成功
在浏览器输入 http://0.0.0.0:4000 ，就可以访问到博客首页

# 三、映射到GitHub
Deployment 这里设置了Git,mocorochio为你的github用户名
修改hexo文件夹下的_config.yml文件，在文件最后面，更改如下：
```xml
deploy:
type: git
repo: git@github.com:xxx/yyy.github.io.git
branch: master
```
这里，“xxx/yyy.github.io.git”表示GitHub上的博客名称路径

接下来是配置
1. 配置本机全局git环境
首先请使用邮箱注册github账号，否则会影响下面操作，记住你注册的邮箱。
另外，请在ubuntu上设置你的git

```shell
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```

生成SSH秘钥
先确定你的VPS 有没有生成过ssh的key，
验证
```shell
ssh -T git@github.com
```
测试添加ssh是否成功。如果看到Hi后面是你的用户名，就说明成功了
```shell
ssh-keygen -t rsa -C xxx@yyy.com
```
xxx@yyy.com为你的邮箱名称
查看 公钥内容 稍后加入Github 账户的 sshkey中

```shell
cat ~/.ssh/id_rsa.pub
```
# 四、Hexo 相关命令
新建文章(会在 hexo/source/_post 下生成对应.md 文件)

```shell
hexo n  post“文章名称”
```
生成静态文件(位于 hexo/public 目录)
```shell
hexo g
```

提交部署(需要相关配置)
```shell
hexo d
```
文章的格式
```markdown
---
title: title #文章标题
date: 2020-04-30 12:34:56 #文章生成时间
categories: "Hexo教程" #文章分类目录 可以省略
tags: #文章标签 可以省略
     - 标签1
     - 标签2
 description: #你对本页的描述 可以省略
---
```


