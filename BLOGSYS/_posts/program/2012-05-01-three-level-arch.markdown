---
layout: post
title: "三层架构是个啥？"
date: 2012-05-01 20:05:01
category: "program"
tags: [三层架构]
---
#### 1.软件体系架构中，一般分层结构：
表示层，业务逻辑层，数据访问层。目的在于提高程序设计及维护效率。

#### 2.请求过程：
表示层接收到用户的数据和请求后，传递给业务逻辑层。  
业务逻辑层接收到用户数据和请求后，先对数据和请求验证和审核，验证过后再将数据和请求传递给数据访问层，验证失败则直接将结果返回表示层。  
数据访问层接收到数据和请求后，开始读取或保存数据。<!-- more -->  

#### 3.反之是响应过程：
数据访问层读取到用户所需数据，然后传递给业务逻辑层。  
业务逻辑层得到数据后，先对结果进行验证，验证有效则将结果传递给表示层。  
表示层接收到结果后，将结果显示在界面。  
