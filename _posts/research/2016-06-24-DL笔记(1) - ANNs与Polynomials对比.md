---
layout: post
title: DL笔记(1) - ANNs与Polynomials对比
date: 2016-06-24 16:48
author: wanghoyle
comments: true
category: Research
tags: Research Math
description: DL笔记(1) - ANNs与Polynomials对比
---
There is no way to know <em>a priori</em> how many hidden neurons are needed for representing a specific system nor there is any idea of the modeling improvement gained when this number is increased. It cannot even be assured that the extracted ANN is unique or that it is the best for a certain number of neurons. This can obviously pose some delicate problems on the ANN predictability, mainly for inputs outside the signal class used for its identification (ANN training).

On the other hand, contrary to the inherent local approximating properties of polynomials, ANNs can behave as global approximants, a potential advantage for modeling strongly nonlinear systems. Also, since the sigmoidal functions used in ANNs are bounded in output amplitude, ANNs do not share the catastrophic degradation of polynomials outside the zone of training. That is, ANNs are, in principle, better in extrapolating beyond the zone where the system was tested during parameter extraction.
