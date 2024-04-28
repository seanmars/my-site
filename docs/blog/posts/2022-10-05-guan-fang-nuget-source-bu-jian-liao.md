---
title: 官方 NuGet Source 不見了
tags:
---

# 官方 NuGet Source 不見了

最近因為重灌 OS 然後安裝 Visual Studio 2022 後開啟舊的 `.NET Core` 專案竟然報說 Package 找不到的問題，但啥都沒動怎麼突然會找不到? Restore 也一樣報說找不到。

後來發現竟然是 Visual Studio 中 NuGet Package Manager 只有 Offline 的來源，官方的竟然不見了，只好手動增加官方 NuGet Source；果然問題就解決了，但重新安裝後竟然預設沒有官方 NuGet Source 真的蠻怪的就是。

以下是新增 NuGet Source 的步驟，順便紀錄一下：

1. 打開 `NuGet Package Manager`
![4j8rwkJUTd](__GHOST_URL__/content/images/2022/10/4j8rwkJUTd.png)
2. 設定 NuGet Source
![NuGet-Package-Manager](__GHOST_URL__/content/images/2022/10/NuGet-Package-Manager.png)

官方最新的 Source URL 可以從 [這邊](https://learn.microsoft.com/en-us/nuget/api/overview) 得到。

---

參考:

- [NuGet Server API](https://learn.microsoft.com/en-us/nuget/api/overview)
- [What is the URL for NuGet Gallery to access (nuget.org) from VS2010?](https://stackoverflow.com/questions/5693139/what-is-the-url-for-nuget-gallery-to-access-nuget-org-from-vs2010)
- 封面圖來源: [ghibli.jp](https://www.ghibli.jp/info/013409/)
