---
layout: post
title: "嵌入式Web服务器boa在ARM平台的移植"
date: 2010-04-08 20:05:01
category: "linux"
tags: [嵌入式,移植]
---
#### 1，下载
http://www.boa.org/

#### 2，解压
```
tar xzf boa-0.94.13.tar.gz
```
<!-- more -->

#### 3，编译
```
cd boa-0.94.13/src
./configure
```
生成了makefile文件，一定要在src目录下，在boa-0.94.12下执行./src/configure后再make可能出错。 
修改makefile文件，把其中的CC=gcc CPP=gcc -E 改为：  

```
CC = arm-linux-gcc  CPP = arm-linux-gcc -E
```

#### 4，然后make（在这一步用3.4.1和3.3.2交叉编译器时均出现如下错误：
```
util.c: 100: 1: pasting “t” and “->” does not give a valid preprocessing token make: [util.o] Error1
```

换成2.95.3交叉编译器后，编译通过。  
另一种解决办法是把compat.h中的 foo##->tm_gmtoff的##去掉。  

#### 5，arm-linux-strip boa 删除调试信息
```
cp boa /nfs
cp ../boa.conf /nfs
cd ../../html/ && cp index.htm test.cgi /nfs
```
在/nfs下修改boa.conf  

```
mount -t nfs 192.168.0.60:/nfs /mnt
```

#### 6.目标板下
```
mkdir /etc/boa && cp /mnt/boa.conf /etc/boa/
cp /mnt/boa /bin/
mkdir /var/log/boa（你也可以在/etc/rc.local中加入一行mkdir /var/log/boa，这样在系统启动时自动创建，而不用人工创建，如果想要让boa在系统启动时也自动运行，那就在/etc/rc.local中再加一行/bin/boa吧）
mkdir -p /var/www/cgi-bin && cd /var/www
cp /nfs/index.html ./
cp /nfs/test.cgi ./
```

#### 7.运行boa，测试
网页文件要显示中文需加上:  

```
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
```
注意用utf-8国际通行的。  

Debian下编译出错解决办法：  
http://www.linux521.com/2009/system/200906/5726.html  
