---
title: 一元函数的定积分
date: 2024-03-22 15:32:18
tags:
- 高等数学
- 积分
---

一元函数的定积分的其中一种定义是函数在闭区间上黎曼和（在每一段子区间的宽度趋于零时）的极限。

黎曼和的引入是为了估计一个函数在某一闭区间上与横坐标轴围成的面积。随着划分愈加精细，这个估计愈加精准。如果在每一段划分的长度趋于零时，所有的划分方案对应的黎曼和都趋于同一个极限，则称这个极限是函数在该闭区间上的定积分。我们将黎曼和 $\displaystyle \sum \dots \Delta x_k$ 演变为符号 $\displaystyle \int \dots dx$ 来表示定积分。

实际上，不定积分的符号是藉由微积分基本定理引入的。符号 $\displaystyle \int$ 符合逻辑的第一次引入应该是在此处。

<!-- more -->

## 黎曼和与定积分

简而言之，黎曼和是对任意闭区间 $[a, b]$ 上的函数 $f$，使用矩形面积的和逼近函数 $f(x)$ 与 $x$ 轴之间的区域的面积。

我们将 $[a ,b]$ 分为 $n$ 个子区间，对每个子区间 $[x_{k-1}, x_k]$ 用 $\Delta x_k = x_k - x_{k-1}$ 表示其宽度，并在子区间内选取一内点 $c_k \in [x_{k-1}, x_k]$，以其坐标 $(c_k, f(c_k))$ 代表整个子区间内所有点的函数值，以这个函数值为矩形的高、以子区间的宽度为矩形的宽，在子区间内放置一个矩形，如下图所示。

{% asset_img riemann-sum.png %}

如果想象矩形能够拥有负值的高，在每个子区间上建立乘积 $c_k \cdot \Delta x_k$，这个乘积代表了每个子区间的矩形的面积。

对所有这些乘积求和，我们称之为黎曼和 $\displaystyle S_p = \sum_{k = 1}^{n} f(c_k) \cdot \Delta x_k$。

每个函数在相同的区间上存在不同的黎曼和，这取决于我们是如何分割区间 $[a ,b]$ 的。如果在每一段子区间的宽度趋于零的不同分割中，得到的黎曼和都收敛于同一个极限，即对于足够精细的所有分割我们都能得到相同的黎曼和，我们可以确信这个和就是函数 $f(x)$ 与 $x$ 轴之间的区域的面积。引入定积分的概念如下：

**定义** 令 $f(x)$ 是定义在 $[a, b]$ 上的函数，称数 $I$ 是 $f$ 在 $[a, b]$ 上的**定积分**，以及 $I$ 是黎曼和 $\displaystyle \sum_{k = 1}^{n} f(c_k) \cdot \Delta x_k$ 的极限，当且仅当 $I$ 满足以下条件：

给定任意数 $\varepsilon > 0$，都存在与之对应的数 $\delta > 0$，使得对于 $[a ,b]$ 的每个具有 $||P|| < \delta$ 的划分 $P = {x_0, x_1, \dots, x_n}$，以及在 $[x_{k-1}, x_k]$ 中任意选取的每个 $c_k$，都成立以下不等式：

$$
|(\sum_{k = 1}^{n} f(c_k) \cdot \Delta x_k) - I| < \varepsilon
$$

在上面的定义中， $\delta$ 指示了划分的宽度需要小到什么程度才能够使黎曼和在允许误差为 $\varepsilon$ 的条件下“收敛”到 $I$。

### 可积函数

严格地证明函数黎曼可积的判断准则，需要利用到*达布上和*、*达布下和*等概念，以及*达布定理*等定理。

简而言之，在黎曼和中，如果我们选取每个子区间的上确界和下确界作为区间内函数值的代表，这样得到的和就是*达布上和*、*达布下和*。

在所有的分割中，达布上和的上确界称为函数在该区间上的*上积分*，达布下和的下确界称为函数在该区间上的*下积分*。

*达布定理*指出当划分的范数 $\lambda \rightarrow 0$ 时，达布上和、达布下和的极限分别是上积分与下积分。

#### 可积的判断准则（充分必要条件）

这些定理的证明可见苏德矿微积分上册附录部分。

**准则1** 设 $f(x)$ 在 $[a, b]$ 上有界，则 $f(x)$ 在 $[a, b]$ 上可积 当且仅当 $f(x)$ 在 $[a, b]$ 上的上积分与下积分相等。

狄利克雷函数在 $[0, 1]$ 上是不可积分的，原因在于在这个区间内，其上积分为 $1$，而下积分为 $0$。

**准则2** 设 $f(x)$ 在 $[a, b]$ 上有界，则 $f(x)$ 在 $[a, b]$ 上可积 当且仅当 对于任意给定的精度 $\varepsilon > 0$，总是存在一个分割 $T$，使得 $f(x)$ 在 $[a, b]$ 上的达布上和 $S(T)$ 与 $f(x)$ 在 $[a, b]$ 上的达布下和 $s(T)$ 之差小于这个任意给定的精度 $\varepsilon$。

**准则3** 设 $f(x)$ 在 $[a, b]$ 上有界，则 $f(x)$ 在 $[a, b]$ 上可积 当且仅当 对于任意给定的精度 $\varepsilon > 0$，总是存在一个分割 $T$，使得 $\displaystyle \sum_{i = 1}^n w_i < \varepsilon$。

这里的 $w_i$ 是每个子区间内函数值的上确界与下确界之差，其几何意义是：当分割足够精细，包围曲线的小矩形面积之和可以足够小。

#### 可积的必要条件

**定理1** 若 $f(x)$ 在闭区间 $[a, b]$ 连续，则 $f(x)$ 在 $[a, b]$ 可积。

证明可由可积的判断准则3得出。

**定理2** 若 $f(x)$ 在闭区间 $[a, b]$ 只有有限个间断点并且有界，则 $f(x)$ 在 $[a, b]$ 可积。

证明同样可由可积的判断准则3得出。

**定理3** 若 $f(x)$ 在闭区间 $[a, b]$ 上单调，则 $f(x)$ 在 $[a, b]$ 可积。

证明同样可由可积的判断准则3得出。

## 微积分基本定理

**积分中值定理** 若 $f$ 是区间 $[a, b]$ 上的**连续函数**，则在区间上至少存在一个点 $c \in [a, b]$ 满足 $\displaystyle f(c) = \frac{1}{b - a}\int_a^b f(x) dx$。

*证明.* 首先证明定积分的最大-最小值不等式，即 $\displaystyle \min_{x \in [a,b]} f \cdot (b - a) \leq \int_a^b f(x) dx \leq \max_{x \in [a,b]} f \cdot (b - a)$。

对于区间 $[a, b]$ 的每一种划分，以及每一个内点 $c_k$ 的选择，都有：

$$
\begin{array}
    \displaystyle \min_{x \in [a,b]} f \cdot (b - a) &= \displaystyle \min_{x \in [a,b]} f \cdot \sum_{k = 1}^n \Delta x_k \\
    &= \displaystyle \sum_{k = 1}^n \min_{x \in [a,b]} f \cdot \Delta x_k \\
    &\leq \displaystyle \sum_{k = 1}^n f(c_k) \cdot \Delta x_k \\
    &= \displaystyle \int_a^b f(x) dx \\
    &= \displaystyle \sum_{k = 1}^n f(c_k) \cdot \Delta x_k \\
    &\leq \displaystyle \sum_{k = 1}^n \max_{x \in [a,b]} f \cdot \Delta x_k \\
    &= \displaystyle \max_{x \in [a,b]} f \cdot \sum_{k = 1}^n \Delta x_k = \max_{x \in [a,b]} f \cdot (b - a)
\end{array}
$$

两边同时除以 $(b - a)$，有：

$$
\min_{x \in [a,b]} f \leq \frac{1}{(b - a)} \int_a^b f(x) dx \leq \max_{x \in [a,b]} f
$$

由连续函数的介值定理，至少存在一个点 $c \in [a, b]$ 满足 $\displaystyle f(c) = \frac{1}{b - a}\int_a^b f(x) dx$。$\blacksquare$

在证明了微积分基本定理之后，我们可以将这个定理中 $c$ 的取值范围进一步收缩到开区间 $(a, b)$，这是藉由微积分基本定理与拉格朗日中值定理证明的。

积分中值定理的几何意义在于，连续函数 $f$ 在任意的闭区间上必定至少取到一次它在这个区间上的平均值 $\bar{f}$。

**微积分基本定理** 若 $f$ 是区间 $[a, b]$ 上的**连续函数**，则 $F(x) = \int_a^x f(t) dt$ 在 $[a, b]$ 上是连续的，并且在 $(a, b)$ 上是可微的，并且它的导数就是 $f(x)$，即 $\displaystyle \frac{d}{dx}\int_a^x f(t) dt = f(x)$。

*证明.* 

$$
\begin{array}
    \displaystyle F'(x) &= \displaystyle \lim_{h \rightarrow 0}\frac{F(x + h) - F(x)}{h} = \lim_{h \rightarrow 0}[\frac{1}{h}(\int_a^{x+h}f(t)dt - \int_a^{x}f(t)dt)] \\
    &= \displaystyle \lim_{h \rightarrow 0}[\frac{1}{h}\int_x^{x+h}f(t)dt]
\end{array}
$$

（第二行的第一个等号成立的原因是定积分是线性算子，可以使用定义证明）

根据积分中值定理，$\displaystyle \frac{1}{h}\int_x^{x+h}f(t)dt$ 在取极限之前是 $f$ 在 $(x, x+h)$ 的取值之一。即：

$$
\begin{array}
    \exist c \in (x, x+h) & s.t. & \frac{1}{h}\int_x^{x+h}f(t)dt = f(c)
\end{array}
$$

由于 $c \in (x, x+h)$，在 $h \rightarrow 0$ 的过程中，$c \rightarrow x$，因此 $\displaystyle \lim_{h \rightarrow 0}f(c) = \lim_{h \rightarrow 0}f(x)$。

由函数 $f(x)$ 的连续性，可知：

$$
\begin{array}
    \displaystyle F'(x) &= \displaystyle \lim_{h \rightarrow 0}\frac{F(x + h) - F(x)}{h} = \displaystyle \lim_{h \rightarrow 0}[\frac{1}{h}\int_x^{x+h}f(t)dt] \\
    &= \displaystyle \lim_{h \rightarrow 0}f(c) = f(x) & \blacksquare
\end{array}
$$

**牛顿-莱布尼兹公式（微积分基本定理第二部分、求值定理）** 若 $f$ 是区间 $[a, b]$ 上的**连续函数**，而 $F$ 是 $f$ 在 $[a, b]$ 上的任意反导数，则有 $\displaystyle \int_a^b f(x) dx = F(b) - F(a)$。

拆分这个定积分到以 $x$ 分割的两个区间上计算，根据微积分基本定理即可证明这个公式。

## 定积分的计算
