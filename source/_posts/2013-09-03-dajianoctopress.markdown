---
layout: post
title: "教你在Github上搭建Octopress博客"
date: 2013-09-03 15:56
comments: false
categories: Github
---
最近几天突然想搭建一个新博客了，之前一直在用新浪博客总感觉没有一种归属感，所以这次便利用Github提供的Pages来搭建一个Octopress开源博客。


* 本次搭建在Win7 x64位下完成，其它操作系统仅供参考


*首先，你需要安装一些环境*

<!-- more -->

下载[Git for Windows](https://code.google.com/p/msysgit/downloads/list?q=full+installer+official+git)并安装
下载[RubyInstaller 1.9.3版本](http://rubyinstaller.org/downloads/)并安装
下载[DevKit-tdm-32-4.5.2](http://rubyinstaller.org/downloads/)并解压缩到绝对英文路径中，建议解压缩到D盘根目录

接下来在`Start Command Prompt with Ruby`命令行中进入DevKit解压缩的目录，然后运行以下命令:
```
ruby dk.rb init
ruby dk.rb install
gem install rdiscount --platform=ruby
```

如果安装成功，就可以使用一些Ruby的工具了，也为后面搭建博客提供了基础环境。

*接下来下载一份Octopress源码*

先通过Git从Github上克隆一份Octopress（在Git Bash上输入命令）

```
git clone git://github.com/imathis/octopress.git octopress
```

Clone完成以后打开Octopress根目录，找到Gemfile，并用编辑器打开，将第一行改成如下
```
source "http://ruby.taobao.org"
```
之后保存即可。
然后安装一些依赖的工具（后面都是在Start Command Prompt with Ruby中输入）

```
cd octopress
gem install bundler
bundle install 
```

安装Octopress默认的Theme，你也可以下载别的主题安装
```
rake install
```

现在你的本地已经有一份完整的Octopress了，只需要将它上传到Github上即可。

你也可以预先使用
```
rake preview
```
命令来预览你的博客，在浏览器中输入`127.0.0.1:4000`来打开

*接下来开始上传博客*

首次上传之前的准备活动

创建 username.github.com 仓库

执行rake setup_github_pages，会提示
```
Repository url
```
把刚才新建的仓库地址输入即可`git@github.com:your name/your name.github.com`

当一切准备完毕以后，运行如下代码即可完成上传
```
rake generate   //生成静态页面
rake deploy     //根据刚才的设置开始上传代码，如果提示权限问题请检查是否添加SSH Key到你的github设置里
接下来把博客源码push上去
git add .       //将仓库所有文件提交跟踪
git commit -m "My blog"//添加更新说明
git push origin source //将源码上传到source分支
```
此时你的博客就已经完成了，等待十分钟左右页面就会出现。

博客地址`your name.github.io`

