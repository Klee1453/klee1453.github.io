---
title: About
layout: about
# toc: true
---

Something about me :)

This page is currently left for draft (or maybe disorganized note pad), about maths, computer sciences, byzantinology, linguistics and so on :)

## About maths

### 极限

Archived to {% post_link single-variable-limit %}.

### （一元函数）微分学

Archived to {% post_link single-variable-derivative %} and {% post_link mean-value-theorem %}.

### （一元函数）积分学

Archived to {% post_link single-variable-indefinite-integration %}, {% post_link single-variable-definite-integration %}, and.

### 泰勒展开

设 $f(x)$ 在 $x = x_0$ 处 $n$ 阶可导，则有：

$$
f(x) = f(x_0) + \sum_{k = 1}^{n}\frac{f^{(k)}(x_0) \cdot (x - x_0)^k}{k!} + o[(x - x_0)^n]
$$

特别地，当 $x_0 = 0$，称此展开式为麦克劳林展开。

当 $n \rightarrow \infty$，称此展开式（此时没有最后的皮亚诺余项）为泰勒级数（麦克劳林级数）。

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

### Git

#### 修改 commit 记录的描述

使用 `git commit --amend` 即可修改上一次 commit 记录的描述。

如果需要修改倒数第 n 个 commit 记录的描述，则需要通过 `git rebase -i` 先变基到 `HEAD~(n+1)`，然后在打开的文本编辑器内找到你想要修改的 commit，将行首的 `pick` 改为 `reword`，这将再次打开一个文本编辑器对选定的 commit 描述进行修改。最后，通过 `git rebase --continue` 回到 `HEAD`，这可能会造成远程仓库的历史记录与本地不一致。

### NPM

- `npm install` 安装 npm 包。使用 `--save` 参数将安装的包添加到 `package.json` 文件的 `dependencies` 列表中，在 npm 5.0.0 及更高版本中， `--save` 选项不再被需要，因为它现在是默认行为。使用 `-g` 参数全局安装。

- `npm list` 查看当前已安装的所有包。这个命令会列出所有已安装的包及其依赖，如果只想查看顶级（也就是直接安装的）包，使用 `npm list --depth=0`。使用 `-g` 参数查看全局安装的包。

- `npm uninstall` 卸载 npm 包。这个命令会从 `node_modules` 目录中删除 npm 包，并且也会从 `package.json` 文件的 `dependencies` 列表中移除它。如果想要同时从 `package.json` 文件的 `devDependencies` 列表中移除它，你可以使用 `-D` 或 `--save-dev` 选项：

### Windows 命令行常用工具以及 Windows Powershell

Windows Powershell 的 Microsoft.PowerShell.Core 管理单元中文文档：

<https://learn.microsoft.com/zh-cn/powershell/module/microsoft.powershell.core>

#### `Get-Command -Name` 获取别名

```ps
PS > Get-Command -Name g++

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Application     g++.exe                                            0.0.0.0    C:\mingw64\bin\g++.exe
```

`(Get-Command -Name g++).Source` 等同于 bash 中的 `which g++`，将在环境变量设置的目录里查找符合条件的文件，返回指令的绝对路径。

#### 计算文件的哈希值

使用 `certutil` 工具。

```ps
PS > certutil -hashfile .\hello.exe SHA256
SHA256 的 .\hello.exe 哈希:
17b6ba1b851e565769ec917b497e60b825f9ee79acd72f3ffed5a66777c79b66
CertUtil: -hashfile 命令成功完成
```

可选的哈希函数有 `MD2`，`MD4`，`MD5`，`SHA1`，`SHA256`，`SHA384`，`SHA512`。

更多选项使用命令 `certutil -hashfile -?` 查看。

### About Linux

#### APT 换源后出现由于没有公钥无法验证下列签名

```bash
root@ub22:/# apt-get update
...
获取:4 http://mirrors.aliyun.com/kali kali-rolling InRelease [41.5 kB]
...
错误:4 http://mirrors.aliyun.com/kali kali-rolling InRelease
  由于没有公钥, 无法验证下列签名: NO_PUBKEY xxxxxxxx
...
正在读取软件包列表... 完成
W: GPG 错误: http://mirrors.aliyun.com/kali kali-rolling InRelease: 由于没有公钥, 无法验证下列签名:  NO_PUBKEY xxxxxxxx
E: 仓库 "http://mirrors.aliyun.com/kali kali-rolling InRelease" 没有数字签名.
N: 无法安全地用该源进行更新, 所以默认禁用该源.
N: 参见 apt-secure(8) 手册以了解仓库创建和用户配置方面的细节.
```

解决方案：`sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv xxxxxxxx`。将 `xxxxxxxx` 替换成报错中的实际公钥。

解决上述报错后，可能会在 `apt-get update` 的时候得到报错：

```bash
W: http://mirrors.aliyun.com/kali/dists/kali-rolling/InRelease: 密钥存储在过时的 trusted.gpg 密钥环中(/etc/apt/trusted.gpg), 请参见 apt-key(8) 的 DEPRECATION 一节以了解详情.
```

需要将密钥从旧的 apt 密钥工具转换为新的 apt 可信密钥格式。

可以先尝试使用 `apt-key list gazebo`，在我遇到的情况下，这将返回与上面的警告类似但更详细的报错信息。

```bash
Warning: apt-key is deprecated. Manage keyring files in trusted.gpg.d instead (see apt-key(8)).
```

使用 `sudo cp /etc/apt/trusted.gpg /etc/apt/trusted.gpg.d` 即可。

## About Byzantine history

### 君士坦丁七世「生于紫室者」《典议论》

### 收藏夹

<https://www.bilibili.com> 上与罗马有关的历史视频。

罗马共和国史：

[【罗马史合集】罗马是如何从城邦变成帝国的？ - 训练有素的将军](https://www.bilibili.com/video/BV1wd4y1h7pP/)

AD 37 - AD 532：

暂缺。

查士丁尼王朝：

[【合集】重现帝国荣光！3个小时看完罗马传奇统帅贝利撒留的一生 - 老喵猫喵](https://www.bilibili.com/video/BV1834y1o7eW/)

AD 565 - AD 641：

暂缺。

希拉克略王朝 & 二十年无政府时期：

[合集·十字路口的东罗马（C.E.641-717） - 青悠闲人](https://space.bilibili.com/358349453/channel/collectiondetail?sid=160823)

伊苏里亚王朝 & 第一次圣像破坏运动：

[合集·变革与斗争中的罗马（C.E.717-802） - 青悠闲人](https://space.bilibili.com/358349453/channel/collectiondetail?sid=924370)

阿莫里亚王朝 & 第二次圣像破坏运动：

[合集·第二次圣像破坏运动（C.E.802-867） - 青悠闲人](https://space.bilibili.com/358349453/channel/seriesdetail?sid=2603754)

AD 867 - AD 1025：

暂缺。

杜卡斯王朝：

[{编年地图史}拜占庭是怎样陷入11世纪危机中的（1）—马其顿王朝末期和伊萨克-科穆宁篇 - 老喵猫喵](https://www.bilibili.com/video/BV11541157j8/)

[杜卡斯家族真的有那么废吗？拜占庭是怎样陷入11世纪危机中的（2）—君士坦丁·杜卡斯&曼齐克特战役篇 - 老喵猫喵](https://www.bilibili.com/video/BV1tZ4y1V7E8/)

[小亚细亚没了！11世纪危机中的拜占庭（3）—“内战内行，外战外行”的杜卡斯 - 老喵猫喵](https://www.bilibili.com/video/BV1zy4y1r7mZ/)

科穆宁王朝 & 第一、第二、第三次十字军东征：

[【合集】一口气看完《阿莱克修斯传》所讲述传奇的拜占庭皇帝阿莱克修斯·科穆宁的一生 - 老喵猫喵](https://www.bilibili.com/video/BV1mN411Q7Mo/)

[【合集】拜占庭帝国的余晖：一口气看完科穆宁王朝1118-1182年的历史 - 老喵猫喵](https://www.bilibili.com/video/BV1J64y18799/)

[【合集】3个小时一口气看完萨拉丁与第三次十字军东征的故事（1169-1192） - 老喵猫喵](https://www.bilibili.com/video/BV1a5411X79T/)

第四次十字军东征 & 尼西亚王朝：

[【合集】地图详解从1204年第四次十字军东征到拉丁帝国建立再到1261年尼西亚帝国重建东罗马帝国的整个过程 - 老喵猫喵](https://www.bilibili.com/video/BV1334y177jM/)

巴列奥略王朝：

[1453年君士坦丁堡的陷落可以避免吗（一） - asherhoa](https://www.bilibili.com/video/BV1J64y1H76W/)

[1453年君士坦丁堡的陷落可以避免吗（二） - asherhoa](https://www.bilibili.com/video/BV1sQ4y1J7tR/)

[1453年君士坦丁堡的陷落可以避免吗（三） - asherhoa](https://www.bilibili.com/video/BV12K411v72Q/)

[1453年君士坦丁堡的陷落可以避免吗（四） - asherhoa](https://www.bilibili.com/video/BV1aW421A7sq/)

奥斯曼帝国：

## About linguistics

### 为常见自然语言编码

ISO 639-1 是国际标准化组织 ISO 639 语言代码标准的第一部分。它含有 184 个两字母的编码，用来标示世界上主要的语言。

这些代码在很多地方都被用作语言的简写，例如：

| | | | | | |
|:-:|:-:|:-:|:-:|:-:|:-:|
| 英语 | en | 中文 | zh | 日语 | ja |
| 法语 | fr | 西班牙语 | es | 意大利语 | it |
| 俄语 | ru | 希腊语 | el | 拉丁语 | la |

详细的列表可以在维基百科中找到：
<https://zh.wikipedia.org/wiki/ISO_639-1>

## About Mahjong

🀇🀇🀇🀈🀉🀊🀋🀌🀍🀎🀏🀏🀏 🀋

天胡、九莲宝灯！

记录一些不太复杂的、以贪心算法为主的麻将策略。

因为是贪心算法，三个重要的部分是：

1. 如何将手牌分割成有限种类型的（所谓基本型与复合型）区块之组合
2. 为上面的基本型与复合型的价值作排序，根据改良与向听数前进的最终目的
3. 当贪心策略间存在冲突，如何抉择

纯粹的贪心算法是不能够实现科学麻将的，然而复杂度得到控制的贪心算法（其实只是一种近似算法）是能够很好地被人类实践的。

不为内容的正确性负责，因为我只是银之间五年老雀士（段位），以及「都是听牌凭什么我弃胡」和「万一他不听这张」理论的坚定拥护者。

### 进攻（牌效率）

所有基本型以及复合型的价值随其数值的变化而变化。

在基本型的情况中，将两面听牌的边界情况 12 以及 89 称为边张，其价值小于其它两面听牌的情况。在复合型中，往往不会特别地为边界情况进行命名区分，然而这个现象是依旧存在的。可以使用递归的算法将其分解为基本型套用基本型两面 vs 边张的结论，然而会增加计算的复杂度。

#### 基本型与复合型

##### ABCD 型

对于四张牌组成的复合型中，ABCD 型无疑是最强的一种，因为它是唯一一种拥有两种不同拆解方式（A + BCD 或者 ABC + D 以及 AB + CD）的四张复合型。

其位于不同位置的价值如下表所示。（结论来自[星野Poteto (´･ω･`) 日麻Ch.](https://www.youtube.com/@poteto_mj_channel)）

需要注意在这张表格中，只写出了当复合型摸到某张数牌后，组成的面子+搭子之搭子部分，而搭子部分按三面 > 两面 > 坎张 > 边张的顺序排序，仅写出顺序最靠前的定义。例如当 1234 摸到 2 时，既可以分解为 123 + 24，又可以分解为 234 + 12，这种情况按上面的规定在对应的元胞中写入坎张，这是因为从形成面子的角度考虑，24 和 12 都是待 3，而 24 的改良机会较 12 更多。

|      | 1   | 2    | 3   | 4    | 5   | 6   | 7    | 8   | 9   | 合计     | 好型  |
| :-:  | :-: | :-:  | :-: | :-:  | :-: | :-: | :-:  | :-: | :-: | :-:     | :-:   |
|    4 |     | 坎张 | 两面 | 对子  | 两面 | 坎张 |     |     |     | 5种19张 | 2种8张 |
| 1234 | 对子 | 坎张 | 两面 | 对子 | 两面 | 坎张 |      |     |     | 6种20张 | 2种7张 |
| 2345 | 两面 | 对子 | 两面 | 两面 | 对子 | 三面 | 坎张 |     |     | 7种24张 | 4种14张 |
| 3456 | 坎张 | 三面 | 对子 | 两面 | 两面 | 对子 | 三面 | 坎张 |     | 8种28张 | 4种14张 |
| 4567 |     | 坎张 | 三面 | 对子 | 两面 | 两面 | 对子 | 三面 | 坎张 | 8种28张 | 4种14张 |
| 5678 |     |     | 坎张 | 三面 | 对子 | 两面 | 两面 | 对子 | 两面 | 7种24张 | 4种14张 |
| 6789 |     |     |      | 坎张 | 两面 | 对子 | 两面 | 坎张 | 对子 | 6种20张 | 2种7张 |
| 6    |     |     |      | 坎张 | 两面 | 对子 | 两面 | 坎张 |     | 5种19张 | 2种8张 |

其价值-位置关系与大部分复合型一致，呈现中心对称关系，最大值出现在 3456 及 4567 处，而越靠近两侧价值越低，其价值略大于单张。

##### AABC 型

ABCC 型与之对称。

|      | 1   | 2    | 3   | 4    | 5   | 6   | 7    | 8   | 9   | 合计     | 好型  |
| :-:  | :-: | :-:  | :-: | :-:  | :-: | :-: | :-:  | :-: | :-: | :-:     | :-:   |
| 1    | 对子 | 边张 | 坎张 |     |     |      |      |     |     | 3种11张 | 0种0张 |
| 1123 | 暗刻 | 边张 | 坎张 | 对子 |     |     |      |     |     | 4种12张 | 1种2张 |
| 2234 | 坎张 | 暗刻 | 两面 | 坎张 | 对子 |     |      |     |     | 5种14张 | 2种5张 |
| 3345 | 坎张 | 两面 | 暗刻 | 两面 | 坎张 | 对子  |      |    |     | 6种20张 | 3种9张 |
| 4456 |      | 坎张 | 两面 | 暗刻 | 两面 | 坎张 | 对子  |    |     | 6种20张 | 3种9张 |
| 5567 |      |     | 坎张 | 两面 | 暗刻 | 两面 | 坎张 | 对子 |     | 6种20张 | 3种9张 |
| 6678 |      |     |     | 坎张 | 两面 | 暗刻 | 两面 | 坎张 | 对子 | 6种20张 | 3种9张 |
| 7789 |      |     |     |     | 坎张 | 两面 | 暗刻 | 两面 | 坎张  | 5种16张 | 3种9张 |

综合来考量，AABC 的价值可以近似地看作单张 A 的价值。AABC 的价值随着手牌中的对子数量的增加而减小。

此外，好型 AAABC 的强度取决于手牌中对子的数量，例如 33345m88s111222z 的手牌将能够听 3m6m8s 的三面听牌，而 33345m78s111222z 却只能够听 6s9s 的两面听牌。一般地讲，当听牌时手牌中包括 AA 在内恰有两对子时，AAABC 的强度将显著提升。而在另一方面，在做牌的时候，如果手牌并不缺对子，那么由于 AA+ABC 这样的分割产生的 AA 对子的价值将不会很高，因为三对子并非是有效率的牌型。

##### ABBC 型

下表仅从牌效率的角度考虑，实际上还可以贪一杯口。

|      | 1   | 2    | 3   | 4    | 5   | 6   | 7    | 8   | 9   | 合计     | 好型  |
| :-:  | :-: | :-:  | :-: | :-:  | :-: | :-: | :-:  | :-: | :-: | :-:     | :-:   |
|   2  | 边张 | 对子 | 两面 | 坎张 |     |      |      |     |     | 4种15张 | 1种4张 |
|    3 | 坎张 | 两面 | 对子 | 两面 | 坎张 |     |      |     |      | 5种19张 | 2种8张 |
| 1223 | 边张 | 对子 | 两面 | 坎张 |     |      |      |     |     | 4种12张 | 1种3张 |
| 2334 | 两面 | 两面 | 对子 | 两面 | 两面 |      |      |     |     | 5种16张 | 4种14张 |
| 3445 |     | 两面 | 两面 | 对子 | 两面 | 两面 |      |      |     | 5种16张 | 4种14张 |
| 4556 |     |     | 两面 | 两面 | 对子 | 两面 | 两面 |       |     | 5种16张 | 4种14张 |
| 5667 |     |     |      | 两面 | 两面 | 对子 | 两面 | 两面  |     | 5种16张 | 4种14张 |
| 6778 |     |     |      |      | 两面 | 两面 | 对子 | 两面 | 两面 | 5种16张 | 4种14张 |
| 7889 |     |     |      |      |      | 坎张 | 两面 | 对子 | 边张 | 4种12张 | 1种3张 |
| 7    |     |     |      |      | 坎张 | 两面 | 对子 | 两面 | 坎张 | 5种19张 | 2种8张 |
|  8   |     |     |      |     |      | 坎张 | 两面 | 对子 | 边张 | 4种15张 | 1种4张 |


##### ABBB 型

##### ACDE 型

B < ACDE < C，例如 2 < 1345 < 3  

#### 基本型之价值比较

三对子拆好型理论、一向听双对子最强理论

#### 要不要棒听即立、听牌时基本型的价值

对于单吊形式的听牌，往往不应该棒听即立，而是应该寻求两面乃至三面听牌的改良，抑或是单吊现物字牌或牌河现物筋牌崁张再进行立直以期提升打点或是提升胡率。

单吊现物字牌 > 引挂双碰 > 现物筋牌崁张 > 中晚巡两面

### 防守

- 现物
- 手役
- 幺九筋牌
- One Chance（OC）
- 早巡外侧（早外）

### 土田浩翔的七对子理论

> 两对就留着，三对可以做，四对准备做，五对一定做

最近痴迷于做七对子（以及四暗刻），学习记录一下日本七对仙人土田浩翔的七对子理论。

**筋牌对子** 只有邻近的筋牌组成的双对子称为筋牌对子。

配牌两对筋牌对子、顺子手搭子极少或是无好型即可尝试直线七对子。

七巡以内，1289 以及字牌在牌河中仅现一张或零张时，应当保留。在需要抉择时，它们的价值应当优先由残余枚数考量，在同等条件下，为字牌 > 19 > 28。

其余的浮牌应当按照是否有希望凑成两对筋牌对子、凑成距离进行考量。5 以及宝牌应当适当保留（不与上述规则冲突时），如果有摸到红宝牌或宝牌的机会。37 应该被优先打出，七对子留牌就是要和常规相反，正常没搭子都要留 37 ，所以 37 更有可能出现在其他人手牌里（所谓金三银七）。

最终在字牌间做抉择时，尤其是随着巡目的推进，应该优先打出没有出现过的字牌，保留现一字牌。

听牌时如果是非字牌听牌，应当优先选择牌河中出现枚数较多的种类，例如 9m2288p14477s4477z 这副牌应当在牌河中万子较多时选择听 9m；而在牌河中索子较多时选择听 1s。

筋牌对子等级理论（麻将牌之间的引力理论）：

```text
11 22 33 44 55 66 77 88 99
4  5  6  7  8  9
          1  2  3  4  5  6
```

当手上摸到 11 对子时，4 更容易成对子，同理有 22 与 5，33 与 6， 44 与 1 和 7 等等。

然而，往往需要形如 114m477p112233s15z 的手牌中抉择 114m 与 477p 的筋牌对子。筋牌对子等级理论为筋牌对子的搭子根据其数字进行排序。

| 筋牌对子等级 | 筋牌对子的搭子 |
| :-: | :-: |
| A | 44-1, 66-9 |
| B | 55-2, 55-8, 22-5, 88-5 |
| C | 11-4, 22-5, 88-5, 99-6 |
| D | 44-7, 66-3 |

其实可以发现，当即将组成筋牌对子的浮牌是 19 或 28 的时候，是最上等的，而 22 与 5 和 88 与 5，则是由于 [todo] 。 而浮牌是 37 则是最恶的情况。

也需要同时考虑场况，土田给出的量化方法是，场上出现很多饼子时，饼子的筋牌对子等级上升一级。