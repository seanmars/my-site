---
title: LinkChecker 測試連結是否有效的工具
tags: python, link, linkchecker, check, valid, tool
---

# LinkChecker 測試連結是否有效的工具

[LinkChecker](https://linkchecker.github.io/linkchecker/index.html) 這個測試連結是否有效的工具是在 [Will 保哥的部落格](https://blog.miniasp.com/post/2023/11/10/Useful-tool-LinkChecker) 那邊看到的工具，蠻好用的就記錄一下。

保哥介紹的蠻詳細的，但剛好我想要一次檢查多個連結的用法保哥沒講到我這邊自己記錄一下。

另外，我是直接安裝在 `Windows` 系統底下的 `Python`，安裝完後如果 `linkchecker` 沒有效可以檢查一下是否把 `Python` 的 Scripts 資料夾加入到環境變數 `Path` 中。

首先建立一個 `txt` 檔案，檔案的第一行一定要寫 `# LinkChecker URL list`，接下來每一行就是一個想測試的 URL，例如 `input.txt`：

    # LinkChecker URL list
    https://www.google.com
    https://www.netflix.com
    https://www.youtube.com
    

接著就使用以下指令來進行測試

    linkchecker --verbose --check-extern -F "html/utf-8/result.html" -o none .\input.txt
    

測試結束後結果就會輸出至 `result.html`

參考:

- [介紹好用工具：使用 LinkChecker 檢查網站連結有效性](https://blog.miniasp.com/post/2023/11/10/Useful-tool-LinkChecker)
- 封面圖來源: [ghibli.jp](https://www.ghibli.jp/info/013409/)
