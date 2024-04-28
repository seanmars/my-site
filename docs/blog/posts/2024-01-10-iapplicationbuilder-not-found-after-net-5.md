---
title: IApplicationBuilder not found After upgrade .NET 5+
---

# IApplicationBuilder not found After upgrade .NET 5+

最近使用 [.NET 8](https://dotnet.microsoft.com) 增加了相關 `IApplicationBuilder` 的 Extension 後發現 `IApplicationBuilder` 被報找不到，IDE 指示增加的參考卻又是絕對路徑的 DLL 檔案相當奇怪，後來找了一圈發現，竟然要安裝 `Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore` 套件後再引入 `Microsoft.AspNetCore.Builder` 才能正常使用 `IApplicationBuilder`。

另外為何是安裝 `Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore`，這個主要是在 [這篇](https://stackoverflow.com/questions/58184170) 有看到相關說沒有 `Microsoft.AspNetCore.Builder` namespace 的事情，也是安裝 `Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore`，所以我推測是否可以安裝這個 package 來達到正確引用沒想到真的是這樣。

PS:

- 本來以前應該是可以安裝 `Microsoft.AspNetCore.Http.Abstractions` 來引用，但是這個 package 現在已經棄用版本也停在 `2.2.0`。

參考:

- [Migrate from ASP.NET Core 3.1 to 5.0](https://learn.microsoft.com/zh-tw/aspnet/core/migration/31-to-50?view=aspnetcore-8.0&amp;tabs=visual-studio)
- [DatabaseDeveloperPageExceptionFilterServiceExtensions.AddDatabaseDeveloperPageExceptionFilter Method](https://learn.microsoft.com/zh-tw/dotnet/api/microsoft.extensions.dependencyinjection.databasedeveloperpageexceptionfilterserviceextensions.adddatabasedeveloperpageexceptionfilter?view=aspnetcore-8.0)
- 封面圖來源: [ghibli.jp](https://www.ghibli.jp/info/013409/)
