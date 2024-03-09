---
title: 一元函数的极限与数列极限
date: 2024-03-04 23:40:18
tags: 
- 高等数学
- 极限
---

## 极限运算的四则运算法则及其推论

若 $\lim f(x) = A,\ \lim g(x) = B$，则有：

- $\lim [f(x) \pm g(x)] = A\pm B$
- $\lim [f(x) \cdot g(x)] = A\cdot B$
- $\displaystyle \lim \frac{f(x)}{g(x)} = \frac{A}{B}$

推论：

- 若 $\lim f(x) = A \neq 0$，则 $\lim [f(x) \cdot g(x)] = A\cdot \lim g(x)$，即俗称的极限中非零因子的极限可以先求
- 若 $\displaystyle \lim \frac{f(x)}{g(x)}$ 存在，并且 $\lim g(x) = 0$，则必有 $\lim f(x) = 0$
- 若 $\displaystyle \lim \frac{f(x)}{g(x)} = A \neq 0$ ，并且 $\lim f(x) = 0$，则必有 $\lim g(x) = 0$

## 常用极限

- 指数函数极限根据底数分类讨论

- 多项式之比的极限抓大头

- $\displaystyle \lim_{x\rightarrow 0} (1 + x)^{\frac{1}{x}} = e$

- $\displaystyle \lim_{x\rightarrow \infty} (1 + \frac{1}{x})^{x} = e$
    - **注意**：$\displaystyle \lim_{x\rightarrow \infty} (1 + x)^{\frac{1}{x}}$、$\displaystyle \lim_{x\rightarrow \infty} (1 + \frac{1}{x})^{x}$ 两式需要注意对于指数函数而言，$-\infty$ 与 $+\infty$ 的函数值不同，因而函数极限不存在（单侧极限存在）。

- $\displaystyle \lim_{x\rightarrow 0} \frac{\alpha^x - 1}{x} = \ln \alpha$

- $\displaystyle \lim_{n\rightarrow \infty} \sqrt[n]{n}= 1$

- $\displaystyle \lim_{n\rightarrow \infty} \sqrt[n]{\alpha}= 1$

$\frac{0}{0}$ 与 $\frac{\infty}{\infty}$ 型极限：洛必达

$0\cdot \infty$ 型极限：取倒数洛必达

$\infty - \infty$ 型极限：通分洛必达

$1\infty$、$\infty^0$、$0^0$ 型：取对数化为$0\cdot \infty$ 型极限洛必达

洛门🙏☦️

对于 $1^\infty$ 形式的极限，若其可写作 $\lim (1 + \alpha(x))^{\beta(x)}$ 之形式，并且 $\alpha(x) \beta(x) \rightarrow A$ ，则有 $\lim (1 + \alpha(x))^{\beta(x)} = e^A$

## 常用的等价无穷小

$$x \rightarrow 0,\ x \sim \sin x \sim \tan x \sim \arcsin x \sim \arctan x \sim \ln (1 + x) \sim e^x - 1$$

- 当 $x \rightarrow 0$ 时，有 $\alpha^x - 1 \sim x \ln \alpha$

- 当 $x \rightarrow 0$ 时，有 $\displaystyle x - \ln (1 + x) \sim \frac{1}{2} x^2$

- 当 $x \rightarrow 0$ 时，有 $\displaystyle 1 - \cos x \sim \frac{1}{2} x^2$

- 当 $x \rightarrow 0$ 时，有 $\displaystyle 1 - \cos^\alpha x \sim \frac{\alpha}{2} x^2$

- 当 $x \rightarrow 0$ 时，有 $\displaystyle x - \sin x \sim \frac{1}{6} x^3$

- 当 $x \rightarrow 0$ 时，有 $\displaystyle \arcsin x - x \sim \frac{1}{6} x^3$

- 当 $x \rightarrow 0$ 时，有 $\displaystyle \tan x - x \sim \frac{1}{3} x^3$

- 当 $x \rightarrow 0$ 时，有 $\displaystyle x - \arctan x \sim \frac{1}{3} x^3$

- 当 $x \rightarrow 0$ 时，有 $(1 + x)^{\alpha} \sim \alpha x$

- 当 $\alpha(x) \rightarrow 0$，$\alpha(x) \cdot \beta(x) \rightarrow 0$ 时，有 $[1 + \alpha(x)]^{\beta(x)} \sim \alpha(x) \cdot \beta(x)$

- 若 $f(x),g(x)$ 在 $U(0)$ 连续，如果有 $f(x) \sim g(x)$，
则有 $\displaystyle \int_0^x f(t) dt \sim \int_0^x g(t) dt$

- 若 $f(x),g(x)$ 在 $U(0)$ 连续，如果有 $f(x) \sim g(x)$，并且 $\lim \varphi(x) = 0$，
则有 $\displaystyle \int_0^{\varphi(x)} f(t) dt \sim \int_0^{\varphi(x)} g(t) dt$

## 等价无穷小的代换法则

- 对于极限式中的因子，如果这个因子的极限为常数，可以将其提取至 $\lim$ 符号外侧

- 作为乘法或除法的因子时，可以无条件代换

- 作为加法或减法的一项时，分别满足以下条件即可代换：
    - 若 $\alpha \sim \alpha_1$，$\beta \sim \beta_1$，并且 $\displaystyle \lim \frac{\alpha_1}{\beta_1} = A \neq -1$，则 $\alpha + \beta \sim \alpha_1 + \beta_1$
    - 若 $\alpha \sim \alpha_1$，$\beta \sim \beta_1$，并且 $\displaystyle \lim \frac{\alpha_1}{\beta_1} = A \neq +1$，则 $\alpha - \beta \sim \alpha_1 - \beta_1$
    - 或者在代换时，需要代入等式 $\alpha = \alpha_1 + o(\alpha_1)$
    - 有些看起来违反这个规则进行代换的情况**是因为它们是先拆再等价无穷小代换的**；而极限能够使用四则运算拆开的前提条件是拆出的两个极限式极限均存在

## 关于无穷小的阶数

- 若 $x \rightarrow 0$ 时 $f(x)$ 是无穷小量，并且 $f'(x)$ 是 $x$ 的 $k$ 阶无穷小（$k > 0$），则 $f(x)$ 是 $x$ 的 $k + 1$ 阶无穷小
    - 使用洛必达法则即可证明

- 若 $f(x)$ 在 $U(0)$ 连续，且当 $x \rightarrow 0$ 时，$f(x)$ 是 $x$ 的 $m$ 阶无穷小，$\varphi(x)$ 是 $x$ 的 $n$ 阶无穷小：则当 $x \rightarrow 0$ 时，$F(x) = \displaystyle \int_{0}^{\varphi(x)} f(t) dt$ 是 $x$ 的 $n \cdot (m + 1)$ 阶无穷小

- 增长速度：反三角函数 < 对数函数 < 幂函数 < 指数函数，往往可用在需要快速判断极限值的时候

## 洛必达法则

若 $f(x),\ g(x)$ 满足：

- $\displaystyle \lim_{x \rightarrow x_0} f(x) = \lim_{x \rightarrow x_0} g(x) = 0$ or $\infty$
- $f(x),\ g(x)$ 在 $U^o(x_0)$ 可导，并且 $g'(x_0) \neq 0$
- $\displaystyle \lim_{x \rightarrow x_0} \frac{f'(x)}{g'(x)} = A$ or $\infty$

则有 $\displaystyle \lim_{x \rightarrow x_0} \frac{f(x)}{g(x)} = \displaystyle \lim_{x \rightarrow x_0} \frac{f'(x)}{g'(x)}$

若 $f(x),\ g(x)$ 满足 $n$ 阶可导，则至多可以使用 $(n - 1)$ 次洛必达法则。

若 $f(x),\ g(x)$ 满足 $n$ 阶连续可导，则至多可以使用 $n$ 次洛必达法则，这是因为连续可推得函数在某点的极限等于函数在某点的函数值。

上面的结论是基于洛必达后极限需要存在的要求，以及函数连续时，可以直接利用 $\displaystyle \lim_{x\rightarrow x_0}f(x) = f(x_0)$ 求极限的性质。然而上面的两个结论并非在所有情况下一定是最恰当的，它实际上缩小了洛必达的可用范围。

## 其他的求极限常用方法

夹逼准则（常用于数列极限）、利用定积分的定义（常用于数列极限，并且往往是 $[0,1]$ 区间）、单调有界定理（常用于由递推式定义的数列极限）

拉格朗日中值定理（常用于极限式中存在结构相似的两项，且不同处夹逼所得之极限存在）
- 可以用此方法证明：当 $\alpha(x) \rightarrow 0,\ \beta(x) \rightarrow 0$ 时，有 $e^{\alpha(x)} - e^{\beta(x)} \sim \alpha(x) - \beta(x)$
