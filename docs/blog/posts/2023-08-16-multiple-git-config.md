---
title: 根據資料夾使用多個 Git Configs
tags: git, gitconfig, multiple
---

# 根據資料夾使用多個 Git Configs

某些時候會因為不同專案造成需要使用不同的 `git config`，以下紀錄該如何在同一台電腦中使用資料夾區分不同的 `git config`，以下使用 user 資訊來做示範：

- Global config > **~/.gitconfig**

    [user]
    	name = user
    	email = user@example.com
    [includeIf "gitdir:~/workspace/"]
      path = ~/workspace/.gitconfig
    

- Config for Work > **~/workspace/.gitconfig**

    [user]
        name = worker
        email = worker@example.com
    

這樣一來只要是在 `workspace` 底下的倉庫都會使用 worker/worker@expamle.com 這個設定來做所有 git 的操作紀錄了。

當然只要是設定在 `.gitconfig` 中的資料都可以依照此種方式來做不同資料夾的設定，例如 alias、color...等

參考:

- 封面圖來源: [ghibli.jp](https://www.ghibli.jp/info/013409/)
