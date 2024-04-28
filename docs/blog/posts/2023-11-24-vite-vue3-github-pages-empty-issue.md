---
title: Vite + Vue3 + GitHub Pages 空白頁的問題
tags: vite, vue3, github, static
---

# Vite + Vue3 + GitHub Pages 空白頁的問題

最近用 Vite + Vue 3 寫了一個小 side project 想直接產出 static website 放上 GitHub pages。

原本想說應該是在簡單不過的事情，沒想到產好後丟上去結果竟然網站整個事空白的。

看了一下 console log 發現是 `asset` 底下的資源讀取不到，看了一下他讀取的網址是錯的。

查了一下資料，因為 `vite.config.js` 中 `base` 的預設值是 `/`，得改成 `./` 才能正確的讀取到 `asset` 底下的資源。

參考:

- 封面圖來源: [ghibli.jp](https://www.ghibli.jp/info/013409/)
