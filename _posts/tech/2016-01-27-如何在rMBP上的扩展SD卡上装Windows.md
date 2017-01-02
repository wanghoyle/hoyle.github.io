---
layout: post
title: 如何在rMBP上的扩展SD卡上装Windows
date: 2016-01-27 19:58
author: wanghoyle
comments: true
category: Tech
tags: Mac Technology Windows
description: 如何在rMBP上的扩展SD卡上装Windows
---
因为工作上的需要，很多软件需要在Win下运行，所以一直在考虑给自己的rMBP上装个Windows。不过机子SSD也就128G大，现在各种软件把空间占据得所剩无几，所以就买了个创见的JetDrive Lite 128G的SD卡插到rMBP上，然后折腾了好久，总算把Windows给装上了。

一开始用Mac下自带的Boot Camp制作了Windows安装U盘，但是在安装界面发现识别不了SD卡。没办法，只能改用大白菜的暴力方法了。之前用大白菜无数次，可以说已经轻车熟路了，很自信能装上。当然不得不说，装的过程非常缓慢，因为小文件实在太多，SD卡的通病就是读写小文件太慢。甚至好多次装一半就出错。后来好不容易装上了，满怀欣喜的开机，然后就一直停在转圈的那个界面，我甚至放了一晚上，早上起来还在转圈，我也是醉了。看来这个方法也不行。

随后在网上看到了<a href="http://bbs.feng.com/forum.php?mod=viewthread&amp;tid=8812965" target="_blank">这篇文章</a>，说直接按传统方法安装到SD卡确实没法启动，建议以VHD模式安装。按照该链接的步骤试了试，总算成功了。

不过，SD卡的小文件读写能力真心很差，特别是安装软件或者安装Windows更新的过程，通常需要数小时甚至一个晚上。当然，除此之外使用起来还挺正常的。
