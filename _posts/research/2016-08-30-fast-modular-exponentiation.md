---
layout: post
title: 大数幂求模 Fast modular exponentiation
date: 2016-08-30 11:49
author: wanghoyle
comments: true
categories: Research
tags: Math Research
description: Fast modular exponentiation
---
问题：求$$({a^b})\% m$$，其中$$a$$,$$b$$,$$m$$可能都是非常大的数（$$>{10^6}$$级别）

## 基本性质：
- $$(a + b)\% m = (a\% m + b\% m)\% m$$.
- $$(a - b)\% m = (a\% m - b\% m + m)\% m$$.
- $$(a \times b)\% m = (a\% m \times b\% m)\% m$$.

对于这种幂指数求模的情况$$({a^b})\% m$$，如果其中的数非常大，特别是指数$$b$$很大的情况下，一般的计算设备都无法直接求出结果，因为$$({a^b})$$可能非常大，超出了计算设备的存储范围（比如长整型最大能表示的数为$$({2^63-1})$$）。这就需要一些技巧来求大数的模。

求解该问题的核心思想是将指数分解为2的整数次幂求和的形式，并使用基本性质3。例如：

假设$$b$$为2的整数次幂的形式$$b = {2^n},n \in {\mathbb{Z}^ + }$$，那么$$(a^{2^n}) \% m = (a^{2^{(n-1)}+2^{(n-1)}}) \% m = (a^{2^{(n-1)}} \times a^{2^{(n-1)}}) \% m = (a^{2^{(n-1)}} \% m \times a^{2^{(n-1)}} \% m) \% m$$。

同理$$(a^{2^{(n-1)}}) \% m = (a^{2^{(n-2)}} \% m \times a^{2^{(n-)}} \% m) \% m$$
...

依次类推，可以得到$$(a^{2^n}) \% m = (\underbrace {a \% m \times \ldots \times a \% m}_{2^n \text{multiplications}})\% m$$

而如果$$b$$不是2的整数次幂的形式，我们可以把$$b$$分解为若干个2的整数次幂求和的形式。比如$$b = 117$$，写成二进制的形式为$$b = (Binary)1110101 = {2^0} + {2^2} + {2^4} + {2^5} + {2^6} = 1 + 4 + 16 + 32 + 64$$，因此，$$({a^b})\% m = ({a^{117}})\% m = ({a^{1 + 4 + 16 + 32 + 64}})\% m = ({a^1}\% m \times {a^4}\% m \times {a^{16}}\% m \times {a^{32}}\% m \times {a^{64}}\% m)\% m$$

	// java example
	public long powMod(long a, long b, long m) {
	    if (m == 1) return 0;
	    if (b == 0) return 1;
	    if (b == 1) return a;
	    long x = powMod(a, b/2, m);
	    x = x * x % m;
	    if(b % 2 == 1) x = x * a % m;
	    return x;
	}

[reference](https://www.khanacademy.org/computing/computer-science/cryptography/modarithmetic/a/fast-modular-exponentiation)
