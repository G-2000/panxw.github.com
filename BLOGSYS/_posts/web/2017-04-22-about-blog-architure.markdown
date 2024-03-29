---
layout: post
title: "谈谈我的博客是如何构建与发布的"
date: 2017-04-22 20:05:01
category: web
tags: [bitbucket, webhook, git, Jekyll]
---
## 1. 概述
最近查看博客服务器的请求日志，发现其中有不少wp-admin.php的错误请求，像是在猜测博客的管理后台，大概认为我这个博客也是Wordpress搭建的吧。那今天就谈谈这个博客构建与发布用到的相关技术。<!-- more -->


## 2. 内容托管
博客起初托管在GitPages，后来发现GitHub上免费帐户无法隐藏文章信息，于是转而放在了Bitbucket上。  
在此要特别为Bitbucket点赞，它家的免费个人帐户可建无限量的私有git仓库，并且单个仓库可支持最多5个成员。


## 3. 构建与发布
#### 3.1 主要用到的技术
1. git，代码同步工具。  
2. Jekyll，站点构建工具。  
3. Webhook，自动部署。  
4. Node.js，Webhook服务。  
5. ssh，加密传输。  

#### 3.2 流程
1. 本地文章更新。  
2. push更新到远程仓库。  
3. 远程仓库收到push后，触发一个请求到Webhook上服务。  
4. Webhook服务验证参数合法性后，pull最新代码到本地仓库。  
5. 调用shell脚本，利用Jekyll生成静态站，然后将新站点更新到发布目录。  
6. 刷新博客查看更新内容。  

#### 3.3安全传输
1. git使用SSH+RSA加密传输。  
2. Webhook使用https+请求参数验证。  


## 4. 总结
博客站是纯静态无任何管理后台的，后期我会关闭php等动态网页服务。  
所以请相关人士不要再猜测后台登录入口了，谢谢啦！