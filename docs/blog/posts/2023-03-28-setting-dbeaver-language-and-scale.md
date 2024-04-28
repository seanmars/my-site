---
title: DBeaver 介面語言以及放大設定
tags: dbeaver, language, ui
---

# DBeaver 介面語言以及放大設定

[DBeaver](https://dbeaver.io/) 是一套免費又好用的資料庫管理工具除了支援跨平台外，支援的資料庫類型也頗多，但不知道 Windows 從哪版開始以後安裝或者更新完就會被強制設定成簡體中文，實在頗困擾的，以下有兩種方式可以強制開啟後使用的介面語言。

1. 在執行檔捷徑後面增加參數 `-nl en`；
2. 則是在 `dbeaver.ini` 設定檔增加參數 `-Duser.language=en`。

`dbeaver.ini` 檔案通常會在以下路徑：`"C:\Users\{user}\AppData\Local\DBeaver\dbeaver.ini"`

另外，如果使用高解析度的螢幕(2K,4K)，有可能會遇到介面圖示、字體過小，導致很難閱讀的狀況，可以在 `dbeaver.ini` 中增加以下指令：

    -Dswt.autoScale=200
    -Dswt.autoScale.method=nearest
    

參考:

- 封面圖來源: [ghibli.jp](https://www.ghibli.jp/info/013409/?ref=seanmars.dev)
