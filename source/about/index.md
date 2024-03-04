---
title: About
layout: about
# toc: true
---

Something about me :)

This page is currently left for draft (or maybe disorganized note pad), about maths, computer sciences, byzantinology, theology, linguistics and so on :)

## About maths

### 极限

#### 常用的等价无穷小

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

#### 等价无穷小的代换法则

- 对于极限式中的因子，如果这个因子的极限为常数，可以将其提取至 $\lim$ 符号外侧

- 作为乘法或除法的因子时，可以无条件代换

- 作为加法或减法的一项时，分别满足以下条件即可代换：
    - 若 $\alpha \sim \alpha_1$，$\beta \sim \beta_1$，并且 $\displaystyle \lim \frac{\alpha_1}{\beta_1} = A \neq -1$，则 $\alpha + \beta \sim \alpha_1 + \beta_1$
    - 若 $\alpha \sim \alpha_1$，$\beta \sim \beta_1$，并且 $\displaystyle \lim \frac{\alpha_1}{\beta_1} = A \neq +1$，则 $\alpha - \beta \sim \alpha_1 - \beta_1$
    - 或者在代换时，需要代入等式 $\alpha = \alpha_1 + o(\alpha_1)$
    - 有些看起来违反这个规则进行代换的情况**是因为它们是先拆再等价无穷小代换的**；而极限能够使用四则运算拆开的前提条件是拆出的两个极限式极限均存在

#### 关于无穷小的阶数

- 若 $x \rightarrow 0$ 时 $f(x)$ 是无穷小量，并且 $f'(x)$ 是 $x$ 的 $k$ 阶无穷小（$k > 0$），则 $f(x)$ 是 $x$ 的 $k + 1$ 阶无穷小
    - 使用洛必达定理即可证明

- 若 $f(x)$ 在 $U(0)$ 连续，且当 $x \rightarrow 0$ 时，$f(x)$ 是 $x$ 的 $m$ 阶无穷小，$\varphi(x)$ 是 $x$ 的 $n$ 阶无穷小：则当 $x \rightarrow 0$ 时，$F(x) = \displaystyle \int_{0}^{\varphi(x)} f(t) dt$ 是 $x$ 的 $n \cdot (m + 1)$ 阶无穷小

### （一元函数）微分学

#### 函数的连续性

函数 $f(x)$ 在 $x = x_0$ 处的连续性按以下法则定义：

- 若 $\displaystyle \lim_{x \rightarrow x_0^-} f(x) = f(x_0)$ 则称函数 $f(x)$ 在 $x = x_0$ 处左连续。

- 若 $\displaystyle \lim_{x \rightarrow x_0^+} f(x) = f(x_0)$ 则称函数 $f(x)$ 在 $x = x_0$ 处右连续。

- 若 $\displaystyle \lim_{x \rightarrow x_0} f(x) = f(x_0)$ 则称函数 $f(x)$ 在 $x = x_0$ 处连续。

- 函数 $f(x)$ 在 $x = x_0$ 处连续当且仅当函数 $f(x)$ 在 $x = x_0$ 处左连续且右连续。

如果函数 $f(x)$ 在 $U^o(x_0)$ 有定义，而在 $x_0$ 不连续，则称 $x_0$ 为函数 $f(x)$ 的一个间断点。 根据函数 $f(x)$ 在 $x_0$ 处的左右极限的存在性与极限值，间断点可以分类为可去间断点$^{(I)}$、跳跃间断点$^{(I)}$、无穷间断点$^{(II)}$和振荡间断点$^{(II)}$。

初等函数及由初等函数进行有限次四则运算及复合得到的函数**在其定义区间内**必然连续。

有限**闭区间**上连续函数满足介值定理、最值定理与零点定理。

**介值定理** 若 $f(x)$ 在 $[a,b]$ 上连续，且 $f(a) \neq f(b)$，则对任意的 $f(a)$ 与 $f(b)$ 之间的值 $C$，均存在至少一个 $\xi \in [a,b]$ 使得 $f(\xi) = C$。

**最值定理** 若 $f(x)$ 在 $[a,b]$ 上连续，则 $f(x)$ 在 $[a,b]$ 上存在最大值 $M$ 和最小值 $m$。

由介值定理与最值定理，可以得到推论： $f(x)$ 在 $[a,b]$ 上连续，则 $f(x)$ 在 $[a,b]$ 上可以取到任何一个介于其最大值与最小值之间的函数值。

**零点定理** 若 $f(x)$ 在 $[a,b]$ 上连续，且 $f(a) \cdot f(b) < 0$，则至少存在一个 $\xi \in [a,b]$ 使得 $f(\xi) = 0$。
零点定理是上面的推论的一个特例。


### （一元函数）积分学

### 泰勒展开

设 $f(x)$ 在 $x = x_0$ 处 $n$ 阶可导，则有：

$$
f(x) = f(x_0) + \sum_{k = 1}^{n}\frac{f^{(k)}(x_0) \cdot (x - x_0)^k}{k!} + o[(x - x_0)^n]
$$

特别地，当 $x_0 = 0$，称此展开式为麦克劳林展开。

当 $n \rightarrow \infty$，称此展开式为泰勒级数（麦克劳林级数）。

由上面的展开式，我们可以得到这样的结论：
$n$ 阶可导的奇函数在零点处的偶数阶导函数值 $f^{(2k)}(0) = 0$，
如果它是$x \rightarrow 0$ 时的无穷小量，它的无穷小阶数必然为奇数阶；
$n$ 阶可导的偶函数在零点处的奇数阶导函数值 $f^{(2k + 1)}(0) = 0$，
如果它是$x \rightarrow 0$ 时的无穷小量，它的无穷小阶数必然为偶数阶。

#### 常用的麦克劳林展开式

$$\displaystyle e^x = 1 + x + \frac{1}{2!} x^2 + \cdots + \frac{1}{n!} x^n + o(x^n)$$

$$\displaystyle \sin x = x - \frac{1}{3!} x^3 + \frac{1}{5!} x^5 + \cdots + (-1)^{n - 1} \cdot \frac{1}{(2n - 1)!} x^{2n - 1} + o(x^{2n - 1})$$

$$\displaystyle \cos x = 1 - \frac{1}{2!} x^2 + \frac{1}{4!} x^4+ \cdots + (-1)^{n} \cdot \frac{1}{(2n)!} x^{2n} + o(x^{2n})$$

$$\displaystyle \ln (1 + x) = x - \frac{1}{2} x^2 + \frac{1}{3} x^3 + \cdots + (-1)^{n - 1} \cdot \frac{1}{n} x^{n} + o(x^{n})$$

$$\displaystyle (1 + x)^\alpha = 1 + \alpha x + \frac{\alpha (\alpha - 1)}{2!} + \cdots + \frac{\alpha(\alpha - 1)(\alpha - n + 1)}{n!} x^{n} + o(x^{n})$$


## About computer sciences

### NPM

- `npm install` 安装 npm 包。使用 `--save` 参数将安装的包添加到 `package.json` 文件的 `dependencies` 列表中，在 npm 5.0.0 及更高版本中， `--save` 选项不再被需要，因为它现在是默认行为。使用 `-g` 参数全局安装。

- `npm list` 查看当前已安装的所有包。这个命令会列出所有已安装的包及其依赖，如果只想查看顶级（也就是直接安装的）包，使用 `npm list --depth=0`。使用 `-g` 参数查看全局安装的包。
