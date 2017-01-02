---
layout: post
title: Gauss-Newton 和 Levenberg-Marquardt 法求解非线性最小二乘问题
date: 2016-04-03 05:53
author: wanghoyle
comments: true
categories: Research
tags: Math Research
description: Gauss-Newton 和 Levenberg-Marquardt 法求解非线性最小二乘问题
---

## 首先回顾标准的牛顿法

**算法** 用牛顿法最小化 $$f\left( {\bf{x}} \right)$$

考虑一个二阶连续可微函数 $$ f\left( {\bf{x}} \right)$$，初始解 $$\bf{x}^0$$，重复以下步骤来计算解序列 $${\bf{x}^1}$$, $${\bf{x}^2}$$, ... 当解序列充分收敛到满足 $$ \nabla f\left({\bf{x}^*} \right) = 0$$ 的一个解时停止。

- 计算梯度 $$ \nabla f\left( {\bf{x}^k} \right)$$ 和海森矩阵 $$ {\bf{H}}\left( {f\left( {\bf{x}^k} \right)} \right)$$。
- 求解 $$ {\bf{H}}\left( {f\left( {\bf{x}^k} \right)} \right)\Delta {\bf{x}} = - \nabla f\left( {\bf{x}^k} \right)$$。
- 令 $$ \bf{x}^{k \rm{ + }1} \rm{ = } {\bf{x}}^k \rm{ + } \Delta \bf{x}$$。
- 令 $$ k = k + 1$$。

----------

用牛顿法最小化 $$ f\left( {\bf{x}} \right)$$ 非常有效，但是也可能不收敛。正如牛顿法求解系统方程一样，算法的收敛性质可以在实际中通过使用先搜索修改模型更新步长来改善。

## 高斯-牛顿法

牛顿法对大部分非线性回归和求逆问题都不直接适用。因为数据点和模型参数可能不相等，方程 $$ {\bf{G}}\left( {\bf{m}} \right) = {\bf{d}}$$ 可能不存在精确解，或者方程 $$ {\bf{G}}\left( {\bf{m}} \right) = {\bf{d}}$$ 有多个解。 这里，我们将使用牛顿法的一个特殊版本来最小化非线性最小二乘问题。

考虑一个非线性系统方程 $$ {\bf{G}}\left( {\bf{m}} \right) = {\bf{d}}$$，$$ {\bf{m}}$$，受限于长度为 $$n$$，有相关指定的标准差的数据向量，$$ {\bf{d}}$$，这个问题是寻找一个长度为 $$n$$ 的参数向量。我们的目标是找到在最小化2范数残差意义下并最佳匹配数据的一组参数。

同线性回归一样，如果我们假设测量误差服从正态分布，那么根据极大似然准则，我们将最小化被标准差归一化后的残差平方和。我们力求最小化加权残差范数
\begin{equation}
  f\left( \bf{m} \right) = \sum\limits_{i = 1}^m {\left( \frac{ G(\bf{m})_i - \bf{d}_i }{ \sigma _i } \right)}^2 \tag{1}
\end{equation}

定义标量函数
\begin{equation}
  f_i\left( \bf{m} \right) = \frac{ G(\bf{m})_i - \bf{d}_i }{ \sigma _i },i = 1,2, \ldots ,m\tag{2}
\end{equation}

以及向量函数
\begin{equation}
  \bf{F} \left( \bf{m} \right) = [ f_1 \left( \bf{m} \right), \ldots, f_m\left( \bf{m} \right) ]^T \tag{3}
\end{equation}

因此
\begin{equation}
  f\left( {\bf{m}} \right) = \sum\limits_{i = 1}^m {f_i \left( \bf{m} \right)^2} = \sum\limits_{i = 1}^m {\left\|\left\| \bf{F} \left( \bf{m} \right) \right\|\right\|_2^2}\tag{4}
\end{equation}

$$ f\left( {\bf{m}} \right)$$ 的梯度可以写为其中每一项的梯度和，然后写成以下矩阵形式
\begin{equation}
  \nabla f\left( \bf{m} \right) = \sum\limits_{i = 1}^m {\nabla \left( {f_i {\left( \bf{m} \right)}^2} \right)} = 2\bf{J}{\left( \bf{m} \right)^T}\bf{F}\left( \bf{m} \right)\tag{5}
\end{equation}

其中 $$ \bf{J}\left( \bf{m} \right)$$ 是 $$ \bf{F}\left( \bf{m} \right)$$ 的雅克比矩阵。与此类似，我们用 $$ f_i\left( \bf{m} \right)$$ 项得到了 $$ f\left( \bf{m} \right)$$ 的海森矩阵。因此
\begin{equation}
  \bf{H}\left( f \left( \bf{m} \right) \right) = 2\bf{J}{\left( \bf{m} \right)^T} \bf{J} \left( \bf{m} \right) + \bf{Q} \left( \bf{m} \right)\tag{6}
\end{equation}

其中
\begin{equation}
  \bf{Q}\left( \bf{m} \right) = 2\sum\limits_{i = 1}^m {f_i \left( \bf{m} \right) \bf{H} \left( {f_i \left( \bf{m} \right)} \right)}\tag{7}
\end{equation}

在**高斯-牛顿（GN）法**中，我们忽略(6)中的 $$ \bf{Q} \left( \bf{m} \right)$$ 项来近似海森矩阵
\begin{equation}
  \bf{H} \left( {f\left( {\bf{m}} \right)} \right) \approx 2{\bf{J}}{\left( {\bf{m}} \right)^T}{\bf{J}}\left( {\bf{m}} \right)\tag{8}
\end{equation}

在非线性回归中，我们期望在接近于最优值 $$\bf{m}^*$$ 时 $$f_i \left( \bf{m} \right)$$很小，以至于在解的领域内这应该是一个合理的近似。相反，对于 $$f_i \left( \bf{m} \right)$$ 很大的非线性最小二乘问题，这就不是一个合理的近似了。

用梯度 $$ \nabla f\left( \bf{m} \right)$$ (5) 和近似的海森矩阵 $$ \bf{H} \left( {f\left( \bf{m} \right)} \right)$$ (8) 来实现牛顿法最小化 $$ f\left( \bf{m} \right)$$，方程两边同时除以2，我们得到
\begin{equation}
  \bf{J} {\left( \bf{m}^k \right)^T} \bf{J} \left( \bf{m}^k \right)\Delta \bf{m} = - \bf{J} {\left( \bf{m}^k \right)^T} \bf{F}\left( \bf{m}^k \right)\tag{9}
\end{equation}

这提供了一个连续求解更新步长 $$ \Delta \bf{m}$$ 的方程。其中 $$n \times n$$ 的矩阵 $$ \bf{J} {\left( \bf{m}^k \right)^T} \bf{J}\left( \bf{m}^k \right)$$ 是对称且半正定的。如果这个矩阵是正定的，那么我们可以用 Cholesky 分解或者其他的满秩方法来求解系统方程并得到 $$ \Delta \bf{m}$$。然而，如果这个矩阵是奇异的，那么这样直接的方法将不可行。尽管在实际中，GN法通常效果很好，但它毕竟是基于牛顿法的，因此也可能因收敛到局部最大值或鞍点 $$ \nabla f\left( \bf{m} \right) \approx 0$$ 或根部不收敛而失败。使用GN及其他这样的迭代方法另一个缺点是：算法可能收敛到局部最小值而不是全局最小值。

## 利文贝格-麦夸特法

在**利文贝格-麦夸特（LM）法**中，GN法模型更新方程 (9) 被修改为
\begin{equation}
  \left( \bf{J} \left( \bf{m}^k \right)^T \bf{J} \left( \bf{m}^k \right) + \lambda \bf{I} \right)\Delta \bf{m} = - \bf{J} {\left( \bf{m}^k \right)^T} \bf{F}\left( \bf{m}^k \right)\tag{10}
\end{equation}

其中大于零的参数 $$ \lambda$$ 在迭代过程中是自适应的以保证收敛。进行如此修改的一个重要原因是为了保证 (10) 式左边的矩阵是非奇异的。因为此时系统方程中的矩阵是对称且正定的，我们可以使用 Cholesky 分解来有效地求解系统模型的更新步长 $$ \delta \bf{m}$$。

对于很大的 $$ \lambda$$,
\begin{equation}
  \bf{J}{\left( \bf{m}^k \right)^T} \bf{J} \left( \bf{m}^k \right) + \lambda \bf{I} \approx \lambda \bf{I}\tag{11}
\end{equation}

那么 (10) 式的解是
\begin{equation}
  \Delta \bf{m} \approx - \frac{1}{\lambda} \nabla f\left( \bf{m} \right)\tag{12}
\end{equation}

这被称为**最速下降**步长，意味着算法简单地沿着使 $$ f\left( \bf{m} \right)$$ 下降最快的负梯度方向前进。最速下降法收敛很慢但是必然收敛到局部最小值。相反，对于很小的 $$ \lambda$$ ，LM法又变回了GN法 (9)，而GN法收敛快但是不一定收敛。

实现LM法的一个挑战是选取 $$ \lambda$$ 的最优值。通常的策略是在GN法效果好的时候使用较小的 $$ \lambda$$ 值，在GN法无法降低残差范数时增大 $$ \lambda$$ 值。一个简单的方法是在开始时使用小的 $$ \lambda$$ 值，而在后面的每一步迭代中自适应。如果LM法导致残差范数减小，那么更新 $$ \bf{m}$$ 并在下次迭代开始前对 $$ \lambda$$ 除以一个常数（比如2），使 $$ \lambda$$ 减小。相反，如果LM方法没有改善解，那么就增加 $$ \lambda$$ 的大小并再试一次，重复这个过程直到模型更新后使得残差范数减小。稳健地实现LM法使用更加复杂的策略来自适应更新 $$ \lambda$$，但即使是这个简单的策略也工作得相当好。

在实际中，小心地使用LM为GN法提供了好的性能以及稳健的收敛性质。同时，LM通常是小、中规模的非线性最小二乘问题所选择的方法。

我们注意到，尽管 (10) 式中LM的稳定因子 $$ \lambda \bf{I}$$ 类似于使用 Tikhonov 正则化的表达式，它并没有改变模型收敛的本质。 $$ \lambda \bf{I}$$ 这一项只是用于改善算法的收敛性能，而没有加入到最小化残差范数的目标函数中，也没有正则化非线性最小二乘问题。
