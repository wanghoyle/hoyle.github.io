---
layout: post
title: Differences between \(l_1\) and \(l_2\) norm
date: 2016-04-16 05:27
author: wanghoyle
comments: true
category: Research
tags: Math Research
description: Differences between \(l_1\) and \(l_2\) norm
---
## Definition:
$$l_1$$-norm, a.k.a. least absolute deviations (LAD), least absolute errors (LAE), and is similar to mean absolute errors (MAE). It is basically minimizing the sum (mean) of the absolute differences (errors) between the target value $$d_i$$ and the estimated values $$f\left(d_i\right)$$:

$$\begin{equation} \sum\limits_{i = 1}^n {| d_i - f\left(d_i\right) |} = {\left\| {\bf{d}} - f\left({\bf{d}}\right) \right\|}_1 \end{equation}$$

$$l_2$$-norm, a.k.a. least squares errors (LSE), and is similar to mean square errors (MSE). It is basically minimizing the sum (mean) of the square of the differences (errors) between the target value $$d_i$$ and the estimated values $$f\left(d_i\right)$$:

$$\begin{equation} \sum\limits_{i = 1}^n {| d_i - f\left(d_i\right) |}^2 = {\left\| {\bf{d}} - f\left({\bf{d}}\right) \right\|}_2^2 \end{equation}$$

## Differences:
- $$l_1$$ regression
  - Not very robust
  - Stable solution
  - Always one solution
- $$l_2$$ regression
  - Robust
  - Unstable solution
  - Possibly multiple solutions

## Robustness:
> The method of least absolute deviations finds applications in many areas, due to its robustness compared to the least squares method. Least absolute deviations is robust in that it is resistant to outliers in the data. This may be helpful in studies where outliers may be safely and effectively ignored. If it is important to pay attention to any and all outliers, the method of least squares is a better choice.

## Stability:
> The instability property of the method of least absolute deviations means that, for a small horizontal adjustment of a datum, the regression line may jump a large amount. The method has continuous solutions for some data configurations; however, by moving a datum a small amount, one could “jump past” a configuration which has multiple solutions that span a region. After passing this region of solutions, the least absolute deviations line has a slope that may differ greatly from that of the previous line. In contrast, the least squares solutions is stable in that, for any small adjustment of a data point, the regression line will always move only slightly; that is, the regression parameters are continuous functions of the data.

## Uniqueness:
$$l_1$$-norm has unique solution whereas $$l_2$$-norm has possibly multiple solutions.

## References:
1. [http://www.chioka.in/differences-between-l1-and-l2-as-loss-function-and-regularization/](http://www.chioka.in/differences-between-l1-and-l2-as-loss-function-and-regularization/)
2. [http://en.wikipedia.org/wiki/Least_absolute_deviations](http://en.wikipedia.org/wiki/Least_absolute_deviations)
