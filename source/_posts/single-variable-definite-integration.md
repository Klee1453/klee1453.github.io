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

**定理2.a** 若 $f(x)$ 在闭区间 $[a, b]$ 只有有限个间断点并且有界，则 $f(x)$ 在 $[a, b]$ 可积。

证明同样可由可积的判断准则3得出。

这个定理有一个更加常用的结论：

**定理2.b** 若 $f(x)$ 在闭区间 $[a, b]$ 只有有限个第一类间断点，则 $f(x)$ 在 $[a, b]$ 可积。

**定理3** 若 $f(x)$ 在闭区间 $[a, b]$ 上单调，则 $f(x)$ 在 $[a, b]$ 可积。

证明同样可由可积的判断准则3得出。

## 微积分基本定理

**积分中值定理** 若 $f$ 是区间 $[a, b]$ 上的**连续函数**，则在区间上至少存在一个点 $c \in [a, b]$ 满足 $\displaystyle f(c) = \frac{1}{b - a}\int_a^b f(x) dx$。

*证明.* 首先证明定积分的最大-最小值不等式，即 $\displaystyle \min_{x \in [a,b]} f \cdot (b - a) \leq \int_a^b f(x) dx \leq \max_{x \in [a,b]} f \cdot (b - a)$。

对于区间 $[a, b]$ 的每一种划分，以及每一个内点 $c_k$ 的选择，都有：

$$
\begin{array}{ll}
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

**微积分基本定理** 若 $f$ 是区间 $[a, b]$ 上的**连续函数**，则 $\displaystyle F(x) = \int_a^x f(t) dt$ 在 $[a, b]$ 上是连续的，并且在 $(a, b)$ 上是可微的，并且它的导数就是 $f(x)$，即 $\displaystyle \frac{d}{dx}\int_a^x f(t) dt = f(x)$。

*证明.* 

$$
\begin{array}{ll}
    \displaystyle F'(x) &= \displaystyle \lim_{h \rightarrow 0}\frac{F(x + h) - F(x)}{h} = \lim_{h \rightarrow 0}[\frac{1}{h}(\int_a^{x+h}f(t)dt - \int_a^{x}f(t)dt)] \\
    &= \displaystyle \lim_{h \rightarrow 0}[\frac{1}{h}\int_x^{x+h}f(t)dt]
\end{array}
$$

（第二行的第一个等号成立的原因是定积分是线性算子，可以使用定义证明）

根据积分中值定理，$\displaystyle \frac{1}{h}\int_x^{x+h}f(t)dt$ 在取极限之前是 $f$ 在 $(x, x+h)$ 的取值之一。即：

$$
\begin{array}{c}
    \exists c \in (x, x+h) & s.t. & \frac{1}{h}\int_x^{x+h}f(t)dt = f(c)
\end{array}
$$

由于 $c \in (x, x+h)$，在 $h \rightarrow 0$ 的过程中，$c \rightarrow x$，因此 $\displaystyle \lim_{h \rightarrow 0}f(c) = \lim_{h \rightarrow 0}f(x)$。

由函数 $f(x)$ 的连续性，可知：

$$
\begin{array}{ll}
    \displaystyle F'(x) &= \displaystyle \lim_{h \rightarrow 0}\frac{F(x + h) - F(x)}{h} = \displaystyle \lim_{h \rightarrow 0}[\frac{1}{h}\int_x^{x+h}f(t)dt] \\
    &= \displaystyle \lim_{h \rightarrow 0}f(c) = \lim_{h \rightarrow 0}f(x) = f(x) & \blacksquare
\end{array}
$$

**牛顿-莱布尼兹公式（微积分基本定理第二部分、求值定理）** 若 $f$ 是区间 $[a, b]$ 上的**连续函数**，而 $F$ 是 $f$ 在 $[a, b]$ 上的任意反导数，则有 $\displaystyle \int_a^b f(x) dx = F(b) - F(a)$。

拆分这个定积分到以 $x$ 为分界的两个区间上计算，根据微积分基本定理即可证明这个公式。

## 定积分的计算

### 利用被积函数的奇偶性

**例1.** 若 $\displaystyle f(x) = \frac{x}{1 + \cos^2 x} - \int_{-\pi}^{\pi} f(x)\sin x dx$，求 $f(x)$

等式两边同时乘以 $\sin x$，然后在 $[-\pi, \pi]$ 积分：

$$
\begin{array}{rl}
    \displaystyle f(x) &= \displaystyle \frac{x}{1 + \cos^2 x} - \int_{-\pi}^{\pi} f(x)\sin x dx \\
    \displaystyle \int_{-\pi}^{\pi} f(x)\sin x dx &= \displaystyle \int_{-\pi}^{\pi} \frac{x\sin x}{1 + \cos^2 x} dx - \int_{-\pi}^{\pi} [\int_{-\pi}^{\pi} f(x)\sin x dx]\sin t dt \\
    &= \displaystyle \int_{-\pi}^{\pi} \frac{x\sin x}{1 + \cos^2 x} dx - 0 \\
    &= \displaystyle 2 \int_{0}^{\pi} \frac{x\sin x}{1 + \cos^2 x} dx \\
    &= \displaystyle \pi \int_{0}^{\pi} \frac{\sin x}{1 + \cos^2 x} dx \\
    &= \displaystyle \pi \int_{0}^{\pi} \frac{-d\cos x}{1 + \cos^2 x} \\
    &= \displaystyle -\pi \arctan \cos x \Big\vert^{\pi}_0 = \frac{\pi^2}{2}
\end{array}
$$

其中第五个等号 $\displaystyle \int_{0}^{\pi} xf(\sin x)dx = \frac{\pi}{2}\int_{0}^{\pi} f(\sin x)dx$ 可以使用区间复现法进行证明。


### 定积分的分部积分法

若 $u = u(x)$，$v = v(x)$ 在 $[a, b]$ 上具有连续导数，则：

$$
\int_a^b u dv = uv |_a^b - \int_a^b v du
$$

**例2.** 证明~~比你们不知道高到哪里去了~~华莱士公式，即：

$$
I_n = \int_0^{\frac{\pi}{2}} \sin^n x dx = \int_0^{\frac{\pi}{2}} \cos^n x dx =
\left\{ \begin{array}{l}
    \displaystyle \frac{n - 1}{n} \cdot \frac{n - 3}{n - 2} \cdots \frac{2}{1} \cdot \frac{\pi}{2}  & (n \in \{2, 4, 6, \dots\}) \\
    \displaystyle \frac{n - 1}{n} \cdot \frac{n - 3}{n - 2} \cdots \frac{3}{2}                      & (n \in \{1, 3, 5, \dots\})
\end{array} \right. 
$$

现证明 $I_n = \int_0^{\frac{\pi}{2}} \sin^n x dx$ 的部分：

$$
\begin{array}{rl}
    \displaystyle \boxed{I_n} = \int_0^{\frac{\pi}{2}} \sin^n x dx 
    &= \displaystyle -\int_0^{\frac{\pi}{2}} \sin^{n - 1}x d\cos x  \\
    &= \displaystyle -\sin^{n - 1}x\cos x |_{0}^{\frac{\pi}{2}} + \int_0^{\frac{\pi}{2}} \cos x d\sin^{n - 1}x \\
    &= \displaystyle -0 + \int_0^{\frac{\pi}{2}} \cos x (n - 1)\sin^{n - 2}x \cos x dx\\
    &= \displaystyle (n - 1)\int_0^{\frac{\pi}{2}}(1 - \sin^2 x)\sin^{n - 2}x dx \\
    &= \displaystyle (n - 1)[\int_0^{\frac{\pi}{2}}\sin^2 x\sin^{n - 2}x dx - \int_0^{\frac{\pi}{2}} \sin^{n}x dx] \\
    &\boxed{\displaystyle (n - 1)I_{n - 2} - (n - 1)I_{n}}
\end{array}
$$

根据上面导出的递推公式 $\displaystyle I_n = \frac{n - 1}{n} I_{n - 2}$，原积分可以递归地计算。下面计算递归的终止情形：

$$
\begin{array}{rl}
    \displaystyle I_1 = \int_0^{\frac{\pi}{2}} \sin x dx 
    &= \displaystyle -\cos x |_0^{\frac{\pi}{2}} \\
    &= \displaystyle 1 \\ \\

    \displaystyle I_2 = \int_0^{\frac{\pi}{2}} \sin^2 x dx 
    &= \displaystyle \frac{2}{1}(\int_0^{\frac{\pi}{2}} \sin^2 x dx + \int_0^{\frac{\pi}{2}} \cos^2 x dx) \\
    &= \displaystyle \frac{2}{1} \cdot \frac{\pi}{2}
\end{array}
$$

而证明 $\displaystyle \int_0^{\frac{\pi}{2}} \sin^n x dx = \int_0^{\frac{\pi}{2}} \cos^n x dx$ 只需要令 $\displaystyle x = \frac{\pi}{2} - t$ 即可得到：

$$
\begin{array}{rl}
    \displaystyle \int_0^{\frac{\pi}{2}} \sin^n x dx 
    &= \displaystyle \int_{\frac{\pi}{2} - 0}^{\frac{\pi}{2} - \frac{\pi}{2}} \sin^n (\frac{\pi}{2} - t) d(\frac{\pi}{2} - t) \\
    &= \displaystyle \int_{0}^{\frac{\pi}{2}} \cos^n t dt & \blacksquare
\end{array}
$$

### 区间复现法

区间复现法是对定积分 $\displaystyle \int_a^b f(x) dx$ 的换元 $x = a + b - t$ ，它将原积分转化为 $\displaystyle \int_a^b f(a + b - t) dt$。

然后，将原积分与换元后得到的积分相加除以二，以达到简化被积函数的目的。

**例3.** 证明：$\displaystyle \int_{0}^{\pi} xf(\sin x)dx = \frac{\pi}{2}\int_{0}^{\pi} f(\sin x)dx$

令 $\displaystyle x = \pi - t$：

$$
\begin{array}{ll}
    \displaystyle \int_{0}^{\pi} xf(\sin x)dx
    &= \displaystyle \int_{0}^{\pi} (\pi - t)f(\sin (\pi - t))dt \\
    &= \displaystyle \int_{0}^{\pi} \pi f(\sin t)dt - \int_{0}^{\pi} t f(\sin t)dt
\end{array}
$$

则：

$$
\begin{array}{ll}
    \displaystyle \int_{0}^{\pi} xf(\sin x)dx
    &= \displaystyle \frac{1}{2}[xf(\sin x)dx + \int_{0}^{\pi} \pi f(\sin x)dx - \int_{0}^{\pi} x f(\sin x)dx] \\
    &= \displaystyle \frac{1}{2} \int_{0}^{\pi} \pi f(\sin x)dx \\
    &= \displaystyle \frac{\pi}{2} \int_{0}^{\pi} f(\sin x)dx
\end{array}
$$


**例4.** 求 $\displaystyle I = \int_{\frac{-\pi}{2}}^{\frac{\pi}{2}} \frac{e^x}{1 + e^x} \sin^4 x dx$

令 $\displaystyle x = - \frac{\pi}{2} + \frac{\pi}{2} - t = -t$：

$$
\begin{array}{ll}
    \displaystyle \int_{\frac{-\pi}{2}}^{\frac{\pi}{2}} \frac{e^x}{1 + e^x} \sin^4 x dx
    &= \displaystyle \int_{\frac{-\pi}{2}}^{\frac{\pi}{2}} \frac{e^{-t}}{1 + e^{-t}} \sin^4 (-t) dt \\
    &= \displaystyle \int_{\frac{-\pi}{2}}^{\frac{\pi}{2}} \frac{1}{e^t + 1} \sin^4 t dt \\
    &= \displaystyle \int_{\frac{-\pi}{2}}^{\frac{\pi}{2}} \frac{1}{e^x + 1} \sin^4 x dx
\end{array}
$$

则：

$$
\begin{array}{ll}
    \displaystyle \int_{\frac{-\pi}{2}}^{\frac{\pi}{2}} \frac{e^x}{1 + e^x} \sin^4 x dx
    &= \displaystyle \frac{1}{2}(\int_{\frac{-\pi}{2}}^{\frac{\pi}{2}} \frac{e^x}{1 + e^x} \sin^4 x dx + \int_{\frac{-\pi}{2}}^{\frac{\pi}{2}} \frac{1}{e^x + 1} \sin^4 x dx) \\
    &= \displaystyle \frac{1}{2}\int_{\frac{-\pi}{2}}^{\frac{\pi}{2}} \sin^4 x dx \\
    &= \displaystyle \int_{0}^{\frac{\pi}{2}} \sin^4 x dx \\
    &= \displaystyle \frac{3}{4} \cdot \frac{1}{2} \cdot \frac{\pi}{2} \\
    &= \displaystyle \frac{3\pi}{16}
\end{array}
$$

**例5.** 求 $\displaystyle I = \int_{0}^{\frac{\pi}{2}} \frac{\sin^p x}{\sin^p + \cos^p x} dx$

令 $\displaystyle x = \frac{\pi}{2} - t$：

$$
\begin{array}{ll}
    \displaystyle \int_{0}^{\frac{\pi}{2}} \frac{\sin^p x}{\sin^p x + \cos^p x} dx 
    &= \displaystyle \int_{0}^{\frac{\pi}{2}} \frac{\sin^p (\frac{\pi}{2} - t)}{\sin^p (\frac{\pi}{2} - t) + \cos^p (\frac{\pi}{2} - t)} dt \\
    &= \displaystyle \int_{0}^{\frac{\pi}{2}} \frac{\cos^p t}{\cos^p t + \sin^p t} dt \\
    &= \displaystyle \int_{0}^{\frac{\pi}{2}} \frac{\cos^p x}{\cos^p x + \sin^p x} dx
\end{array}
$$

则：

$$
\begin{array}{ll}
    \displaystyle \int_{0}^{\frac{\pi}{2}} \frac{\sin^p x}{\sin^p x + \cos^p x} dx 
    &= \displaystyle \frac{1}{2}(\int_{0}^{\frac{\pi}{2}} \frac{\sin^p x}{\sin^p x + \cos^p x} dx + \int_{0}^{\frac{\pi}{2}} \frac{\cos^p x}{\cos^p x + \sin^p x} dx) \\
    &= \displaystyle \frac{1}{2} \int_{0}^{\frac{\pi}{2}} \frac{\sin^p x + \cos^p x}{\sin^p x + \cos^p x} dx \\
    &= \displaystyle \frac{\pi}{4}
\end{array}
$$

## 变限积分

### 变限积分的性质

#### 连续性

根据微积分基本定理的前半部分，若 $f$ 是区间 $[a, b]$ 上的连续函数，则 $\displaystyle F(x) = \int_a^x f(t) dt$ 在 $[a, b]$ 上是连续的。

#### 可导性

根据微积分基本定理的前半部分，若 $f$ 是区间 $[a, b]$ 上的连续函数，则 $\displaystyle F(x) = \int_a^x f(t) dt$ 在 $(a, b)$ 上是可微的。

如果 $f$ 不是区间 $[a, b]$ 上的连续函数，但是区间 $[a, b]$ 上的可积函数，则：
- 在 $f$ 的可去间断点 $x_0$ 处， $\displaystyle F(x) = \int_a^x f(t) dt$ 可导，$\displaystyle F'(x_0) = \lim_{x\rightarrow x_0} f(x)$。
- 在 $f$ 的跳跃间断点 $x_0$ 处， $\displaystyle F(x) = \int_a^x f(t) dt$ 连续但不可导，$\displaystyle F'_-(x_0) = \lim_{x\rightarrow x_0^-} f(x)$，$\displaystyle F'_+(x_0) = \lim_{x\rightarrow x_0^+} f(x)$。

借助变限积分 $\displaystyle \int_0^x f(t) dt$ 的几何意义就能方便地记忆上面（有关第一类间断点的）结论。

可能产生误解的地方在于，从几何意义上看，函数 $\displaystyle F(x) = \int_0^x f(t) dt$ 是连续的，但它仍然可能是不可导的，就像 $F(x) = |x|$ 在 $x = 0$ 的情况一般。

另外，几何直觉上的光滑*曲线*对应的是导函数连续，即 $f(x)$ 是光滑的，就是 $f'(x)$ 是连续的。

有关 $f$ 的震荡间断点处 $\displaystyle \int_a^x f(t) dt$ 的连续性、可导性问题），参见：

[Integral of functions that have oscillating discontinuous points(not finite) aren't differentiable? - StackExchange](https://math.stackexchange.com/questions/4533179/integral-of-functions-that-have-oscillating-discontinuous-pointsnot-finite-are)

[The primitive of a discontinuous function? - StackExchange](https://math.stackexchange.com/questions/95700/the-primitive-of-a-discontinuous-function)

[How to prove the continuity of [integral with variable bounds of non-continuous function] at essential (but not infinite) discontinuity point? - StackExchange](https://math.stackexchange.com/questions/4886706/how-to-prove-the-continuity-of-integral-with-variable-bounds-of-non-continuous)

实际上，只要 $f(x)$ 是有界的，就一定有函数 $\displaystyle F(x) = \int_0^x f(t) dt$ 是连续的。下面给出证明：

*证明.* 欲证 $F(x)$ 在 $x_0$ 连续，即证 $\displaystyle \lim_{x\rightarrow x_0}F(x) = x_0$，根据极限的 $\varepsilon-\delta$ 定义，这个极限式可以改写为：

$$
\begin{array}{c}
    \forall \varepsilon > 0,\quad \exists \delta > 0 & s.t. & \forall x \in (x_0 - \delta, x_0 + \delta),\quad |F(x) - F(x_0)| < \varepsilon
\end{array}
$$

我们可以证明，对于任意的可积函数 $g(x)$ 及其一个原函数 $G(x)$，有：

$$
|G(x_1) - G(x_2)| = |\int_{x_1}^{x_2} g(x) dx| \leq (x_2 - x_1) \max_{x\in (x_1, x_2)} |g(x)| 
$$

我们对 $[x, x_0]$ 应用这个不等式：

$$
|F(x) - F(x_0)| \leq (x_0 - x) \max_{x\in D_f} |f(x)| 
$$

对于任意给定的 $\varepsilon > 0$，令 $\displaystyle (x_0 - x) \max_{x\in D_f} |f(x)| = \varepsilon$，这意味着，我们找到了邻域的（一侧）边界 $\displaystyle x_a = x_0 - \frac{\displaystyle \max_{x\in D_f} |f(x)|}{\varepsilon}$，在这个边界上，有：

$$
|F(x_a) - F(x_0)| \leq (x_0 - x_a) \max_{x\in D_f} |f(x)| = \varepsilon
$$

而对于 $x \in (x_a, x_0)$ 的所有 $x$，我们都有：

$$
|F(x) - F(x_0)| \leq (x_0 - x) \max_{x\in D_f} |f(x)| < (x_0 - x_a) \max_{x\in D_f} |f(x)| = \varepsilon
$$

对于邻域的另一侧，我们也能以相同的方式找到边界 $x_b$，这样，我们就能找到上面极限式中所需要的 $\delta$：在邻域 $U(x_0, \delta)$ 内，一定有 $|F(x) - F(x_0)| < \varepsilon$，这也就证明了 $\displaystyle F(x) = \int_0^x f(t) dt$ 在 $x_0$ 的连续性。$\blacksquare$

#### 奇偶性

与导函数奇偶性变换规律一致。

设 $f(x)$ 是连续函数，若 $f(x)$ 是偶函数，则 $\displaystyle F(x) = \int_0^x f(t) dt$ 是奇函数。

若 $f(x)$ 是奇函数，则 $\displaystyle F(x) = \int_0^x f(t) dt$ 是偶函数，并且对于任意实数 $a$， $\displaystyle F(x) = \int_a^x f(t) dt$ 也是偶函数。

### 变限积分的导数计算

设法利用微积分基本定理。

利用换元法处理积分上下限不是 $\displaystyle \int_a^x$ 的情况。

对于积分 $\displaystyle \int_a^{\varphi(x)} f(t) dt$：

对 $F(\varphi (x)) = \displaystyle \int_a^{\varphi(x)} f(t) dt$ 使用微积分基本定理，有：

$$
\frac{d}{dx} \int_a^{\varphi(x)} f(t) dt = f[\varphi(x)] \cdot \varphi'(x)
$$

对于积分 $\displaystyle \int_{\psi(x)}^{\varphi(x)} f(t) dt$：

先将其拆分为两个部分，分别使用换元法计算，则有：

$$
\begin{array}{rl}
    \displaystyle \frac{d}{dx} \int_{\psi(x)}^{\varphi(x)} f(t) dt 
    &=\displaystyle \frac{d}{dx} [\int_{a}^{\varphi(x)} f(t) dt + \int_{\psi(x)}^{a} f(t) dt] \\
    &=\displaystyle \frac{d}{dx} [\int_{a}^{\varphi(x)} f(t) dt] - \frac{d}{dt}[\int_{a}^{\psi(x)} f(t) dt] \\
    &=\displaystyle f[\varphi(x)] \cdot \varphi'(x) - f[\psi(x)] \cdot \psi'(x)
\end{array}
$$

对于积分 $\displaystyle \int_{a}^{x} f(x, t) dt$ 较简单的情形，可以利用凑微分（第一类换元法）解决被积函数内包含 $x$ 的情况，例如：

$$
\begin{array}{rl}
    \displaystyle \frac{d}{dx} \int_a^x \sin(x - t) dt
    &= \displaystyle \frac{d}{dx} [-\int_a^x \sin(x - t) d(- t + x)] \\
    &= \displaystyle -\sin x
\end{array}
$$

一般地，对于 $\displaystyle \frac{d}{dx} \int_a^b f(x, y) dy$，如果 $f$ 在 $[a, b]\times [c, d]$ 连续，$f_x$ 在 $[a, b]$ *一致连续*，则可以交换求导符号 $\displaystyle \frac{d}{dx}$ 与积分号，有：

$$
\frac{d}{dx} \int_c^d f(x, y)dy = \int_c^d \frac{\partial f(x, y)}{\partial x} dy
$$

*证明.*

$$
\begin{array}{rl}
    \displaystyle \frac{d}{dx} \int_c^d f(x, y)dy
    &= \displaystyle \lim_{\Delta x\rightarrow 0} \frac{\int_c^d f(x + \Delta x, y)dy - \int_c^d f(x, y)dy}{\Delta x} \\
    &= \displaystyle \lim_{\Delta x\rightarrow 0} \int_c^d \frac{f(x + \Delta x, y) - f(x, y)}{\Delta x} dy
\end{array}
$$

由 $f$ 的连续性，使用拉格朗日中值定理，有：

$$
\begin{array}{rl}
    \displaystyle \frac{d}{dx} \int_c^d f(x, y)dy
    &= \displaystyle \lim_{\Delta x\rightarrow 0} \int_c^d \frac{f(x + \Delta x, y) - f(x, y)}{\Delta x} dy \\
    &= \displaystyle \lim_{\Delta x\rightarrow 0} \int_c^d \frac{\partial f}{\partial x}(x + \theta \Delta x, y) dy,\quad \theta \in (0, 1)
\end{array}
$$

由于 $f_x$ 在 $[a, b]$ *一致连续*，因此对于任意给定的 $\varepsilon > 0$，都存在 $\delta > 0$，使得当 $|\Delta x| < \delta$ 时，有：

$$
\displaystyle \Big \vert \frac{\partial f}{\partial x}(x + \theta \Delta x, y) - \frac{\partial f(x, y)}{\partial x} \Big \vert < \varepsilon 
$$

因此，对其在 $[c, d]$ 上积分，有：

$$
\displaystyle \int_c^d \Big \vert \frac{\partial f}{\partial x}(x + \theta \Delta x, y) - \frac{\partial f(x, y)}{\partial x} \Big \vert dy < (d - c)\varepsilon
$$

并且：

$$
\begin{array}{rl}
    \displaystyle \Big \vert \int_c^d \frac{\partial f}{\partial x}(x + \theta \Delta x, y) dy -  \int_c^d \frac{\partial f(x, y)}{\partial x} dy \Big \vert
    &= \displaystyle \Big \vert \int_c^d [\frac{\partial f}{\partial x}(x + \theta \Delta x, y) - \frac{\partial f(x, y)}{\partial x}] dy \Big \vert \\
    &\leq \displaystyle \int_c^d \Big \vert \frac{\partial f}{\partial x}(x + \theta \Delta x, y) - \frac{\partial f(x, y)}{\partial x} \Big \vert dy\\
    &< (d - c)\varepsilon
\end{array}
$$

这就根据定义证明了等式左侧极限的值为 $\displaystyle \int_c^d \frac{\partial f(x, y)}{\partial x} dy$，原命题得证。$\blacksquare$

参见：
[含参量积分基础知识(1) 正常积分部分 - 知乎](https://zhuanlan.zhihu.com/p/436737350)
[关于极限，求导，积分能否换序的讨论](https://zhuanlan.zhihu.com/p/667864334)

更一般地，对于 $\displaystyle \int_{\psi(x)}^{\varphi(x)} f(x, t) dt$ ，如果 $f$ 在 $[a, b]\times [c, d]$ 连续，$f_x$ 在 $[a, b]$ *一致连续*，并且 $\varphi(x)$ 与 $\psi(x)$ 可导，将其视作复合函数 $H(x, \varphi(x), \psi(x))$ ，利用复合函数求导法则可以得到：

$$
\begin{array}{rl}
    \displaystyle \frac{d}{dx} \int_{\psi(x)}^{\varphi(x)} f(x, t) dt 
    &= \displaystyle \frac{\partial H}{\partial x} + \frac{\partial H}{\partial \varphi} \cdot \frac{\partial \varphi}{\partial x} + \frac{\partial H}{\partial \psi} \cdot \frac{\partial \psi}{\partial x} \\
    &= \displaystyle \int_{\psi(x)}^{\varphi(x)} \frac{\partial f(x, t)}{\partial x} dt + f(x, \varphi(x)) \cdot \varphi'(x) + f(x, \psi(x)) \cdot \psi'(x)
\end{array}
$$