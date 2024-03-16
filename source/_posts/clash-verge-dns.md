---
title: 为 Clash Verge 设置内网 DNS 策略
date: 2024-02-29 11:34:33
tags:
- clash
- clash verge
- 代理
---

在部分网络环境中，可能存在只有内网 DNS 服务器能够解析的内网域名或屏蔽了外网 DNS 。
一般情况下，订阅提供的配置使用了公共DNS，这可能导致无法访问内网域名，需要设置 Clash 的 DNS 。

这种无法访问的情况可以在 Clash 的日志中确定：

<!-- more -->

{% asset_img log.png %}

解决方案是在订阅配置的以下字段的**最前面**加上内部网络域名的 DNS 策略。

```yaml
  nameserver-policy:
    +.internal.crop.com:    # <- 需要修改为实际内网域名,使用 "," 分割多个域名
    - "system"              # <- 或者修改为实际内网 DNS
```

可以使用以下域名通配符以便于匹配：

**通配符`*`** - Clash 的通配符`*`只能匹配一级域名，例如`*.xxx.edu.cn`只能够匹配`git.xxx.edu.cn`而不能匹配`user.git.xxx.edu.cn`。

**通配符`+`** - Clash 的通配符`+`可以匹配多个或零个级别，例如`+.xxx.edu.cn`匹配`xxx.edu.cn`，`git.xxx.edu.cn`,`user.git.xxx.edu.cn`等等。

**通配符`.`** - Clash 的通配符`.`可以匹配多个级别，例如`+.xxx.edu.cn`匹配`git.xxx.edu.cn`,`user.git.xxx.edu.cn`等等。


也可以使用下面的脚本来自动化这个设置，在 Clash Verge 中，你需要在订阅页面点击新建，选择类型为 Script 的订阅并启用，随后点击右上角的重新激活订阅。

```js
// Define the `main` function

function main(params) {
  if (!params.dns) {
    params.dns = {};
  }

  const nameserverPolicy = {};
  nameserverPolicy["+.internal.crop.com"] = [
    "system"
  ];

  const rawNameserverPolicy = params.dns["nameserver-policy"] ?? {};
  for (let prop in rawNameserverPolicy) {
    if (!nameserverPolicy.hasOwnProperty(prop)) {
      nameserverPolicy[prop] = rawNameserverPolicy[prop];
    }
  }

  params.dns["nameserver-policy"] = nameserverPolicy;

  return params;
}
```

需要注意的是，`nameserver-policy`字段的覆盖关系是从上到下的，如果你的订阅存在其他的`nameserver-policy`策略，那么必须要将上面的设置放置于`nameserver-policy`最前方。否则将被你的订阅的其他策略覆盖，例如下图中的 DNS 服务器并没有使用预期的`10.10.0.21`。

{% asset_img wireshark.png %}