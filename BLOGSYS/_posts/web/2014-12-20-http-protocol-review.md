---
layout: post
title: "HTTP请求/响应构成"
date: 2014-12-20 20:05:01
category: "web"
tags: [HTTP]
---
#### 1.客户端HTTP请求
请求行+若干请求头+请求数据。  
请求行：请求方式+资源名称+HTTP版本号。  
请求头：描述客户端请求主机及客户机的环境。  
请求数据：多个请求头与请求数据之间用空行分割。<!-- more -->  

请求方式：GET/POST等7种。  
GET数据附在url中，最大容量1K。POST数据则放在请求数据中，容量无限制。  

#### 2.服务端HTTP响应
状态行+若干响应头+响应数据。  
状态行：HTTP版本号+状态码+状态说明。  
响应头：描述服务器基本信息及数据处理方式。  
响应数据：若干响应头与响应数据之间用空行分割。  
