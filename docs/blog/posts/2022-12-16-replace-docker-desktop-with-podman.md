---
title: 使用 Podman 代替 Docker Desktop
tags: docker, podman, pull
---

# 使用 Podman 代替 Docker Desktop

因為 Docker Desktop 現在不能繼續免費商用([官方公告](https://www.docker.com/blog/updating-product-subscriptions/))，所以找了替代的產品 [Podman](https://podman.io/) + [Podman Desktop](https://podman-desktop.io/) 來使用。

不過剛安裝好 pull 就遇到問題，主要是 pull source 需要一些改變，可以從 [官方文件](https://docs.podman.io/en/latest/markdown/podman-pull.1.html) 看到，如果需要從 Docker 的官方 Hub pull image 需要在前面增加 `docker://` 來明確指定。

---

參考:

- 封面圖來源: [ghibli.jp](https://www.ghibli.jp/info/013409/)
