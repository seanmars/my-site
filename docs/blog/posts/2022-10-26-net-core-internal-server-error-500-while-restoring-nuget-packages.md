---
title: .Net Core Internal Server Error 500 while restoring NuGet packages
---

# .Net Core Internal Server Error 500 while restoring NuGet packages

為了在 linux 測試，所以使用 WSL (Windows Subsystem for Linux) 的 Debain 來測試。

結果在 `dotnet restore` 的時候遇到 `Internal Server Error 500` ，最後發現原因是專案有使用 `NuGet.Config` 這個設置檔案，而裡面因為在 Windows 上只需要增加自定義的 package server 就可以使用，但在 Linux 環境似乎會有問題；從 [官方網站](https://learn.microsoft.com/en-us/nuget/consume-packages/configuring-nuget-behavior) 推論是因為 Solution 有放 `NuGet.Config` 就會 ***overridden*** User 層級的設定檔。

解決辦法就是把官方的 package server 加入到 `NuGet.Config` 檔案中

    <?xml version="1.0" encoding="utf-8"?>
    
    <configuration>
        <packageSources>
            <add key="nuget.org" value="https://api.nuget.org/v3/index.json" protocolVersion="3" />
            <add key="custom-server" value="http://nuget.custom-server.net/v3/index.json" />
        </packageSources>
    </configuration>
    

然後使用 `dotnet restore` 的時候還需要多增加參數

    dotnet restore --configfile /path-of-NuGet.Config
    

看 [官方網站](https://learn.microsoft.com/en-us/nuget/consume-packages/configuring-nuget-behavior) 給的行為模式，應該是不需要特定指定設定檔，不過不給就是會噴錯，就只好指定了。

---

參考:

- [官方網站](https://learn.microsoft.com/en-us/nuget/consume-packages/configuring-nuget-behavior)
- [Document which settings from NuGet.config affect dotnet restore](https://github.com/dotnet/docs/issues/6496)
- 封面圖來源: [ghibli.jp](https://www.ghibli.jp/info/013409/)
