---
title: 一元函数的不定积分
date: 2024-03-17 15:13:51
tags:
- 高等数学
- 积分
---

这是险恶的撬棍符号 $\displaystyle \int$ 的第一次出现。

**定义** 对于函数 $f(x)$，如果存在某个可微函数 $F(x)$ 对定义区间 $I$ 上的所有 $x$，都有 $F'(x) = f(x)$，则称 $F(x)$ 为函数 $f(x)$ 的**反导数**或**一个原函数**。函数 $f(x)$ 的所有反导数（或称原函数，下文中统一称为原函数）称为函数 $f(x)$ 的**不定积分**，用记号 $\displaystyle \int f(x) dx$ 表示，$\displaystyle \int$ 是积分号，$x$ 是积分变量，$f$ 是被积函数。

可以粗略地认为，对变量 $x$ 的不定积分运算 $\displaystyle \int \dots dx$ 是求导运算 $\displaystyle \frac{d}{dx}$ 的逆运算。

<!-- more -->

## 原函数的存在性

若函数 $f(x)$ 在区间 $I$ 上连续， 则 $f(x)$ 在区间 $I$ 上必有原函数。

若函数 $f(x)$ 在区间 $I$ 上有第一类间断点， 则 $f(x)$ 在区间 $I$ 上必没有原函数。

## 原函数与不定积分

由定义我们可以知道，如果 $F(x)$ 是 $f(x)$ 的一个原函数，那么显然 $F(x) + C$ 也是 $f(x)$ 的原函数。并且，除了这些函数以外，$f(x)$ 不会存在其他的原函数，下面将给出简要的证明。

*证明.* 我们首先证明两个引理：

**[中值定理系1]** 假设函数 $f(x)$ 在 $(a, b)$ 可导（$a,\ b$ 可取 $\pm \infty$），若 $\forall x \in (a, b)$，都有 $f'(x) = 0$，则对 $\forall x \in (a, b)$，都有 $f(x) = C$，其中 $C$ 是常数。

*证明.* 任取 $x_1 < x_2 \in (a, b)$，必然有 $f(x)$ 在 $[x_1, x_2]$ 连续、在 $(x_1, x_2)$ 可导。

对 $f(x)$ 在区间 $(x_1, x_2)$ 上使用拉格朗日中值定理，有 $\displaystyle \frac{f(x_1) - f(x_2)}{x_1 - x_2} = f'(\xi) = 0$，其中 $\xi$ 是介于 $x_1$ 与 $x_2$ 的一点。

因此，对于 $\forall x_1, x_2 \in (a, b)$，我们都能够证明 $f(x_1) = f(x_2)$，从而证明了 $f(x)$ 在区间 $(a, b)$ 上是一个常函数。$\blacksquare$

**[中值定理系2]** 假设函数 $f(x),\ g(x)$ 在 $(a, b)$ 可导（$a,\ b$ 可取 $\pm \infty$），并且 $\forall x \in (a,b)$ 都有 $f'(x) = g'(x)$，则存在某个常数 $C$，使得 $f(x) = g(x) + C$。

*证明.* 由导数的运算法则，可知 $[f(x) - g(x)]' = f'(x) - g'(x) = 0$。

由[中值定理系1]的结论，可知存在某个常数 $C$ 使得 $f'(x) - g'(x) = C$，即 $g'(x) = f'(x) + C$。$\blacksquare$

现在我们考虑原问题，假设 $G(x)$ 也是 $f(x)$ 的一个原函数，那么必然有 $G'(x) = f(x)$。

由于 $F(x)$ 是 $f(x)$ 的一个原函数，因此 $G'(x) = f(x) = F'(x)$。

根据[中值定理系2]，可知存在某个常数 $C_1$ 使得 $G(x) = F(x) + C_1$，这也就是说除了 $F(x) + C$以外，$f(x)$ 不会存在其他的原函数。$\blacksquare$

不定积分结果（**在形式上**）不唯一，求导即可验证积分结果的正确性。然而不同形式的不定积分结果之间，一定只相差一个任意常数。

有很大一部分的不定积分并不能通过使用常规的方法求解原函数，但这并不意味着这些函数不存在原函数（由于这些函数都符合不定积分存在性的要求，不能够说这些不定积分“不可积”），只是它们的原函数并不是初等函数。几个常见的不存在初等函数解的不定积分如下：

$$
\begin{array}{c}
    \displaystyle \int e^{x^2} dx & 
    \displaystyle \int \frac{\sin x}{x} dx &
    \displaystyle \int \frac{\cos x}{x} dx &
    \displaystyle \int \frac{1}{\ln x} dx &
    \dots
\end{array}
$$

在上面的积分中，如果我们定义 $\displaystyle \int \frac{\cos x}{x} dx = \Ci(x)$（实际上三角积分函数 $\Ci(x)$ 是通过变上限积分定义的），那么我们就可以用它来计算其他的一些不存在初等函数解的不定积分，例如：

$$
\begin{array}{ll}
    \displaystyle \int \sin\frac{1}{x} dx & 
    = \displaystyle x\sin\frac{1}{x} - \int x d\sin\frac{1}{x} \\

    &= \displaystyle x\sin\frac{1}{x} - \int x \cos\frac{1}{x} d\frac{1}{x} \\
    &= \displaystyle x\sin\frac{1}{x} - \int \frac{\cos\frac{1}{x}}{\frac{1}{x}} d\frac{1}{x} \\
    &= \displaystyle x\sin\frac{1}{x} - \Ci(x)
\end{array}
$$

## 不定积分的运算法则

### 分部积分法

## 不定积分的计算

### 凑微分（第一类换元法）

### 换元法（第二类换元法）

### 常见类型的不定积分

#### 有理函数分式的不定积分

#### 三角函数的不定积分