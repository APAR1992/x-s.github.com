---
layout: post
title: " Android开发环境搭建之sun-java6-jdk"
date: 2013-09-04 17:57
comments: true
categories: Android
---
* 现在的Ubuntu源默认已经没有sun-java6的安装包了
* 所以需要手动添加一条源来安装

<!-- more -->
*方法如下：

1、添加这个源：
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse。

方法：
```
sudo gedit /etc/apt/sources.list
```
打开源列表，在最后一行添加
```
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
```

保存退出。

2、sudo apt-get update

3、sudo apt-get install sun-java6-jdk

中途会出两个对话框，都选OK，安装完后可以查看版本，如果看到如下信息再说明安装OK