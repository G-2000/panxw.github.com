---
layout: post
title: "eclipse下Egit rebase 步骤"
date: 2012-11-26 20:05:01
category: "git"
tags: [eclipse,Egit]
---
1.提交修改文件  

```
Team->commit
``

2.更新仓库文件  

```
Team->Fetch-from-Upstream
```<!-- more -->

3.Rebase, 修改冲突文件  

```
Team->Rebase,(fix diff)
```

4.修改文件添加至索引  

```
Team->Add to index
```

5.继续Rebase  

```
Team->Rebase->continue rebase
```

6.Push到服务器  

```
Team->Push-to-Upstream
```
