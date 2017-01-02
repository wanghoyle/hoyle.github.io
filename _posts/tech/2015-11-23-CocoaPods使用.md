---
layout: post
title: CocoaPods使用
date: 2015-11-23 11:53
author: wanghoyle
comments: true
category: Tech
tags: iOS Link Technology
description: CocoaPods使用
---
<ul>
	<li>
<h3><strong>查看当前ruby版本：</strong></h3>
</li>
</ul>

[shell]ruby -v[/shell]

<ul>
	<li>
<h3><strong>更新ruby源：</strong></h3>
</li>
</ul>

[shell]
gem sources --remove https://rubygems.org/
gem sources -a https://ruby.taobao.org/ 
gem sources -l
[/shell]

<ul>
	<li>
<h3><strong>下载安装CocoaPods：</strong></h3>
</li>
</ul>

[shell]sudo gem install cocoapods[/shell]

<ul>
	<li>
<h3><strong>使用CocoaPods：</strong></h3>
</li>
</ul>
<ol>
	<li>cd到项目总目录</li>
	<li>建立Podfile，终端输入：

[shell]vim Podfile[/shell]

</li>
	<li>键盘输入 i，进入编辑模式，输入：

[text]
platform :ios, '7.0'
pod 'MBProgressHUD', '~&gt; 0.8'
[/text]

</li>
	<li>然后按Esc，并且输入“:”号进入vim命令模式，然后在冒号后边输入wq</li>
	<li>终端输入：

[shell]pod install[/shell]

</li>
	<li>通过ProjName.xcworkspace打开工程（而不是ProjName.xodeproj）</li>
</ol>
<ul>
	<li>
<h3><strong>CocoaPods可以查找你想要的第三方库：</strong></h3>
</li>
</ul>

[shell]pod search UI[/shell]

