---
title: About
layout: about
---

Something about me :)

This page is currently left for draft (or maybe disorganized note pad), about maths, computer sciences, byzantinology, theology, linguistics and so on :)

## About maths

### 极限

#### 等价无穷小

- 当 $x \rightarrow 0$ 时，有 $1 - \cos x \sim \frac{1}{2} x^2$

- 当 $x \rightarrow 0$ 时，有 $1 - \cos^\alpha x \sim \frac{\alpha}{2} x^2$

- 当 $x \rightarrow 0$ 时，有 $(1 + x)^{\alpha} \sim \alpha x$

- 当 $\alpha(x) \rightarrow 0$，$\alpha(x) \cdot \beta(x) \rightarrow 0$ 时，有 $[1 + \alpha(x)]^{\beta(x)} \sim \alpha(x) \cdot \beta(x)$

- 如果有 $f(x) \sim g(x)$，则有 $\int_0^x f(t) dt \sim \int_0^x g(t) dt$

- 如果有 $f(x) \sim g(x)$，并且 $\lim \varphi(x) = 0$，则有 $\int_0^{\varphi(x)} f(t) dt \sim \int_0^{\varphi(x)} g(t) dt$

#### 无穷小的阶数

- 若 $x \rightarrow 0$ 时 $f(x)$ 是无穷小量，并且 $f'(x)$ 是 $x$ 的 $k$ 阶无穷小（$k > 0$），则 $f(x)$ 是 $x$ 的 $k + 1$ 阶无穷小
    - 使用洛必达定理即可证明

- 若 $f(x)$ 在 $U(0)$ 连续，且当 $x \rightarrow 0$ 时，$f(x)$ 是 $x$ 的 $m$ 阶无穷小，$\varphi(x)$ 是 $x$ 的 $n$ 阶无穷小：则当 $x \rightarrow 0$ 时，$F(x) = \int_{0}^{\varphi(x)} f(t) dt$ 是 $x$ 的 $n \cdot (m + 1)$ 阶无穷小

### （一元函数）微分学

### （一元函数）积分学

## About computer sciences

### NPM

- `npm install` 安装 npm 包。使用 `--save` 参数将安装的包添加到 `package.json` 文件的 `dependencies` 列表中，在 npm 5.0.0 及更高版本中， `--save` 选项不再被需要，因为它现在是默认行为。使用 `-g` 参数全局安装。

- `npm list` 查看当前已安装的所有包。这个命令会列出所有已安装的包及其依赖，如果只想查看顶级（也就是直接安装的）包，使用 `npm list --depth=0`。使用 `-g` 参数查看全局安装的包。
