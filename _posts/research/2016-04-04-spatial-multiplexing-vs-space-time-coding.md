---
layout: post
title: Spatial multiplexing vs. Space–time coding
date: 2016-04-04 20:58
author: wanghoyle
comments: true
category: Research
tags: MIMO Research
description: MIMO techniques
---
<p style="text-align: justify;">Spatial multiplexing: 空间复用，与信道容量（数据率 data rate）有关。
Space–time coding: 空时编码，与信道的多样性（diversity）有关。</p>
<p style="text-align: justify;">A MIMO system can provide two types of gains: diversity gain and spatial multiplexing gain [1].
一个MIMO系统提供两种增益：多样性增益及空间复用增益［1］。</p>
<p style="text-align: justify;">Current transmission schemes over MIMO channels typically fall into two categories: data rate maximization or diversity maximization schemes [2].
现有的基于MIMO信道的传输方案可归为两类：最大化数据率 或 最大化多样性［2］。</p>
<p style="text-align: justify;">Given a MIMO channel, both gains can, in fact, be simultaneously obtained, but there is a fundamental tradeoff between how much of each type of gain any coding scheme can extract: higher spatial multiplexing gain comes at the price of sacrificing diversity [1].
给定一个MIMO信道，两种增益实际上可以同时得到，但是任意的编码方式能得到每种增益的多少是有一个基本的折中：更高的空间复用增益需要以牺牲多样为代价［1］。</p>
<p style="text-align: justify;">Effectively, each TX antenna then sees a differently encoded, fully redundant version of the same signal. In this case, the multiple antennas are only used as a source of spatial diversity and not to increase data rate, or at least not in a direct manner [2].
每一路发射天线都能看作同一个信号经过不同编码而完全冗余的版本。在这种情况中，多天线只是用作空间复用源而不会提高数据率，至少不能直接提高［2］。</p>
<p style="text-align: justify;">Spatial multiplexing can be regarded as a special class of STBCs (space–time block codes) where streams of independent data are transmitted over different antennas, thus maximizing the average data rate over the MIMO system [2].
空间复用可以被看作STBC（空时块编码）的特例，不相关的数据流通过不同的天线被传输，这样来提高MIMO系统的平均数据率［2］。</p>
<p style="text-align: justify;"><strong>Reference</strong></p>
<p style="text-align: justify; padding-left: 30px;">[1] L. Zheng and D. N. C. Tse, "Diversity and multiplexing: a fundamental tradeoff in multiple-antenna channels," <em>IEEE Transactions on Information Theory</em>, vol. 49, no. 5, pp. 1073-1096, May 2003.
[2] D. Gesbert, M. Shafi, Da-shan Shiu, P. J. Smith and A. Naguib, "From theory to practice: an overview of MIMO space-time coded wireless systems," <em>IEEE Journal on Selected Areas in Communications</em>, vol. 21, no. 3, pp. 281-302, Apr 2003.</p>
