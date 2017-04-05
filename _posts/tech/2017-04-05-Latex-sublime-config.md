---
layout: post
title: 在Sublime上配置Latex环境
date: 2017-04-05 23:30
author: wanghoyle
comments: true
category: Tech
tags: Technology
description: 在Sublime上配置Latex环境
---

# 准备工作

1. Sublime 3 (神级编辑器，请自行度娘下载地址)
2. TexLive (LaTex 编译工具，推荐 TexLive 或 MikTex，都是跨平台的)
3. Sumatra PDF (可选。如果你用的是 Windows 操作系统，则推荐安装 Sumatra PDF，轻量级 PDF 预览工具，支持反向搜索和不关闭软件时编译)

请确定已经安装了最新的 Sublime 3，及 LaTex 编译工具，下面开始介绍配置流程。


# Sublime 3 中配置 LaTex 环境

1.打开 Sublime，打开命令输入面板：

    Win 下按 ctrl+shift+p
    Mac 下按 command+shift+p

2.输入 `package install`，选择第一项

3.稍等片刻，在新的输入框中输入 `latexTools`，选择第一项安装

4.这样 Sublime 的 LaTex 插件就装好了，重启 LaTex

5.选择 Preferences -> Package Settings -> LaTexTools -> Settings-User，这就打开了自定义的配置文件

6.按 `ctrl+F` 搜索 `windows`（Mac 用户搜索 `osx`，Linux用户搜索 `linux`，不过 Mac 和 Linux 下一般不用修改）

7.`texpath` 后输入 Latex 编译环境的安装路径，以 TexLive 32位默认为例，输入：

    C:\\Program Files\\texlive\\2013\\bin\\win32;$PATH


# 配置 Sumatra PDF (可选，仅限 Windows 用户)

1.接着上一步，将自定义配置文件中的 `sumatra` 后的值修改为 Sumatra PDF 的安装路径

2.将 Sumatra PDF 的主程序目录添加到环境变量PATH，这一步很重要，否则下一步会无法进行。

3.打开命令提示符，执行以下命令：（将其中的安装路径替换成你实际的安装路径）

    sumatrapdf.exe -inverse-search "\"C:\Program Files\Sublime Text 3\sublime_text.exe\" \"%f:%l\""


# 使用

进行到现在，理论上应该就已经配置好了。以后就可以用 Sublime 写 LaTeX 了。写完之后保存（新建的文件一定要先保存，否则 build 是无效的），然后按下快捷键 `ctrl+B`，Sublime 就会自动调用 LaTeXTools 的 build 系统来进行编译，然后自动打开 Sumatra PDF 进行预览。之后每次修改后只要 `ctrl+B` 一下，Sumatra PDF 里的内容就会自动更新。同时在 Sumatra PDF 中双击相应的内容，会调到 Sublime 中对应的位置。

