---
title: 为 git 设置代理
date: 2024-02-29 11:42:53
tags:
- git
- 代理
---

往往 git 并不会使用系统代理，这时需要手动指定 git 使用 `${protocol}://localhost:${port}` 作为代理服务器。

<!-- more -->

如果使用的是 Clash，可以在设置中找到 Clash 提供的 socks5 与 http 端口。

使用下面的命令设置全局 git 的代理。

```bash
$ git config --global http.proxy ${protocol}://localhost:${port}
```

git 的配置有三个级别：system，global与local，分别对应系统，当前用户与当前仓库。

也可以指定只对某些地址使用代理（例如`https://github.com`）。

```bash
$ git config --global http.https://github.com.proxy ${protocol}://localhost:${port}
```

需要注意的是，**实际上 git 的代理配置并不存在 `https.proxy` 选项**，可以从 git 的文档中查看更多与此相关的内容：<https://git-scm.com/docs/git-config#Documentation/git-config.txt-httpproxy>。

如果 git 的代理设置并没有按预期运行，可以使用下面的命令查询 git 的所有配置，查看是否有冲突的配置。

```bash
$ git config --global --list
```

另外可以使用下面的命令查询某一项配置（例如`http.proxy`）。

```bash
$ git config --global --get http.proxy
```