---
layout: post
title: "Android 之Parcelable使用例子"
date: 2012-06-12 20:05:01
category: "android"
tags: [Parcelable]
---
关于Android中的Parcelable：  
1.Android推荐实现Parcelable接口而非Seriable接口来实现对象的序列化。  
2.但当Parcelable中含有列表List时，则要求列表中的信息类是Seriable的。  
3.Parcelable接口实现类除了必须实现writeToParcel(Parcel dest, int flags)方法外(describeContents()默认即可)，还需创建一个类型为Parcelable.Creator< T > 名为CREATOR的public静态变量(createFromParcel(Parcel source) 方法也是必须的)。  

Github：<https://github.com/allthelucky/android-develop-kits/tree/master/ParcelableTest>  
