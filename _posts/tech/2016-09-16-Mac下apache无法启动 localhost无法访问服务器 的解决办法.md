---
layout: post
title: Mac下apache无法启动 localhost无法访问服务器 的解决办法
date: 2016-09-16 17:35
author: wanghoyle
comments: true
category: Tech
tags: Mac Technology
description: Mac下apache无法启动 localhost无法访问服务器 的解决办法
---
# 问题描述
由于删除了 <span style="color: #ff99cc;">/private/var/log </span>下面的日志，导致重启电脑后apache无法正常工作。

# 删除log的初衷是
当系统用久了，日志文件占据了几十个G的硬盘容量。

# 造成的后果
重启电脑后apache无法正常运行，访问localhost或127.0.0.1都会无法找到服务器。

# 解决方法是

 在log目录下，新建一个名为apache2的文件夹，之后系统会自动在apache2里面重新生成apache需要的日志，便可正常访问和使用apache服务了。

    $ sudo mkdir /private/var/log/apache2

 然后重启apache

	$ sudo apachectl restart

 启动Apache

    启动：
	$ sudo apachectl start

	停止：
	$ sudo apachectl stop

	重启：
	$ sudo apachectl restart

# 查看 Apache 版本：

	$ httpd -v

浏览器打开 [http://127.0.0.1](http://127.0.0.1) 或 [http://localhosts/](http://localhosts/) 可以看到 It works! 的页面

对应的文件目录是：
<span style="color: #ff99cc;">/Library/WebServer/Documents/</span>
