---
title: 现代希腊语的拉丁转写
date: 2024-03-07 10:21:05
tags:
- ellinika
---

如何使用拉丁字母书写现代希腊语 以及 如何将拉丁字母书写的语言改用希腊字母书写。

<!-- more -->

现代希腊语的拼写与发音是非单射但满射的，能够实现严格的一字一音。

#### 辅音

|||||||
|:-:|:-:|:-:|:-:|:-:|:-:
$\pi$ | p, /p/ | $\tau$ | t, /t/ | $\kappa$ | k, /k/
$\mu \pi$ | b, /b/ |$\nu \tau$ | d, /d/ | $\gamma \kappa$ | g, /ɡ/
$\varphi$ | f, /f/ | $\theta$ | th, /θ/ | $\chi$ | ch, /x/
$\beta$ | v,/v/ | $\delta$ | dh?, /ð/ | $\gamma$ | gh?, /ɣ/
$\sigma$ | s, /s/ | $\zeta$ | z, /z/
$\mu$ | m, /m/ | $\nu$ | n, /n/
$\rho$ | r, /ɾ/| $\lambda$ | l, /l/
$\psi$ | ps, /ps/ | $\tau\sigma$ | ts, /ts/ | $\xi$ | ks, /ks/
| | | $\tau\zeta$ | tz, /tz/ | 
| | | | |$\gamma\gamma$ | g, /ɡ/

注意，在上表中，$(\gamma\kappa,\gamma\gamma)$ 在词首仅可使用 $\gamma\kappa$。

现代希腊语中存在大量的以上辅音组成而成的双辅音乃至三辅音组合，如表所示。

> [TODO]
>
> 将下面的表格转为二维索引的表格

| | |
|:-:|:-:|
$\pi-$ | $\pi\lambda, \pi\nu, \pi\rho, \pi\tau$
$\tau-$ | $\tau\mu, \tau\rho$
$\kappa-$ | $\kappa\lambda, \kappa\rho, \kappa\tau$
$\mu\pi-$ | $\mu\pi\rho$
$\nu\tau-$ | $\nu\tau\rho$
$\gamma\kappa-$ | $\gamma\kappa\lambda, \gamma\kappa\rho$
$\varphi-$ | $\varphi\theta, \varphi\lambda, \varphi\rho, \varphi\tau$
$\theta-$ | $\theta\nu, \theta\lambda, \theta\mu, \theta\rho$ 
$\chi-$ | $\chi\theta, \chi\lambda, \chi\nu, \chi\rho, \chi\tau$
$\beta-$ | $\beta\gamma, \beta\delta, \beta\lambda, \beta\rho$
$\delta-$ | $\delta\rho$
$\gamma-$ | $\gamma\lambda, \gamma\nu, \gamma\rho$
$\sigma-$ | $\sigma\beta, \sigma\gamma, \sigma\kappa, \sigma\kappa\lambda, \sigma\lambda, \sigma\mu, \sigma\pi, \sigma\tau, \sigma\tau\rho, \sigma\phi, \sigma\chi$
$\zeta-$ | /
$\mu-$ | $\mu\nu, \mu\pi\rho$
$\nu-$ | $\nu\delta\rho$
$\rho-$ | /
$\lambda-$ | /
$\psi-$ | /
$\tau\sigma-$ | /
$\xi-$ | /
$\tau\zeta-$ | /


#### 元音

|||
|:-:|:-:|
|$\iota$, $\eta$, $\varepsilon\iota$, \\ $\upsilon$, $\omicron\iota$, $\upsilon\iota$|i, /i/|
|$\varepsilon$, $\alpha\iota$|e, /e/|
|$\alpha$|a, /a/|
|$\omicron$, $\omega$|o, /o/|
|$\omicron\upsilon$|u, /u/|

#### 特例

对于元音、辅音组合 $\alpha\upsilon$ 与 $\varepsilon\upsilon$，它们的发音取决于它们的下一个读音，如果它们随后的读音是清辅音（$\pi,\tau,\kappa,\varphi,\theta,\chi, \sigma,\xi,\psi$）或是空集（位于词尾），则发音为 /af/ 以及 /ef/；如果他们随后的读音是浊辅音，则发音为 /av/ 以及 /ev/。

#### 希腊字母书写 -> 拉丁字母书写

可以通过一个简单的贪心算法实现将单词分割成音素（虽然不严谨）。

1. 遇到辅音字母开头的串，贪心地将辅音字母加入当前音素，即向后包括尽可能多的辅音字母，直到遇到元音字母。
2. 辅音字母后的第一个合法元音组合跟随这个辅音字母加入当前音素。
3. 遇到元音字母开头的串，如果后面不是 则当前音素终止。
4. 单词末尾的 是可以接受的，它们独立成为一个音素。

#### 拉丁字母书写 -> 希腊字母书写