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
## 查看当前ruby版本

	ruby -v

## 更新ruby源

	gem sources --remove https://rubygems.org/
	gem sources -a https://ruby.taobao.org/ 
	gem sources -l

## 下载安装CocoaPods

	sudo gem install cocoapods

## 使用CocoaPods

- cd到项目总目录
- 建立Podfile，终端输入：

	vim Podfile

- 键盘输入 i，进入编辑模式，输入：

	platform :ios, '7.0'
	pod 'MBProgressHUD', '~&gt; 0.8'

- 然后按Esc，并且输入“:”号进入vim命令模式，然后在冒号后边输入wq
- 终端输入：

	pod install

- 通过ProjName.xcworkspace打开工程（而不是ProjName.xodeproj）

## CocoaPods可以查找你想要的第三方库

	pod search UI
