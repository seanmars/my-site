---
title: Windows 11 VPN by L2TP/IPSec with PSK 無法連線的問題
---

# Windows 11 VPN by L2TP/IPSec with PSK 無法連線的問題

這問題應該是 Windows 本來就有，但之前按照 [如何透過 Windows 電腦連線至 Synology VPN Server？](https://kb.synology.com/zh-tw/DSM/tutorial/How_do_I_connect_to_Synology_VPN_Server_via_Windows_PC) 這篇，把相關的 register 更新後就可以了。

`Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\PolicyAgent` 把 `AssumeUDPEncapsulationContextOnSendRule` 改為 `2(十六進位)`。

但不知道為啥最近 2024-04-10 的時候被 OS 強制更新後就無法連上 VPN 了；本來以為只是更新後設定跑掉，但把網路設定 reset 跟確認 register 也沒錯後，還是無法連上。

最後只能走反安裝更新了，一開始從 `Start > Settings > Windows Update > Update history > Uninstall updates` 挑了最近更新的 package 反安裝，依序 `KB5036620 > KB5036893 > KB5034467 > KB5035853` 反安裝重開機後，突然就可以連上 VPN 了，但是詭異的是我重開機一次後又不行了，於是又把 Windows 更新打開，發現可以安裝 `KB5035967`、`KB5036620`、`KB5036893` 這三個，安裝後重開機又可以連上了(整個莫名其妙)，但發現唯一沒有更新的是 `KB5034467`、`KB5035853`，然後另外安裝到了 `KB5035967`，整個搞不懂為啥，總之最後又可以連線了。

推測不知道是不是前後的 package 有衝突導致的。

### 2024-04-27 更新狀況

2024-04-27 不知為何突然的又無法連上 VPN，後來發現 `KB5036893` 這個更新不知道為啥又被安裝回來，明明已經點了延後更新，解決方法就是去歷史更新反安裝後就又正常可以連線了。

Ref:

- [kb5035853](https://support.microsoft.com/en-us/topic/march-12-2024-kb5035853-os-builds-22621-3296-and-22631-3296-a69ac07f-e893-4d16-bbe1-554b7d9dd39b)
- [kb5036620](https://support.microsoft.com/en-us/topic/april-9-2024-kb5036620-cumulative-update-for-net-framework-3-5-and-4-8-1-for-windows-11-version-22h2-and-windows-11-version-23h2-20c41b49-cd82-4fed-a1b1-0e9ce5a21b5d)
- [kb5036893](https://support.microsoft.com/en-us/topic/april-9-2024-kb5036893-os-builds-22621-3447-and-22631-3447-a674a67b-85f5-4a40-8d74-5f8af8ead5bb)
- [kb5034467](https://support.microsoft.com/en-us/topic/february-13-2024-kb5034467-cumulative-update-for-net-framework-3-5-and-4-8-1-for-windows-11-version-22h2-and-windows-11-version-23h2-dc19c781-bae4-4c66-bff0-143be84ac99d)
- [如何透過 Windows 電腦連線至 Synology VPN Server？](https://kb.synology.com/zh-tw/DSM/tutorial/How_do_I_connect_to_Synology_VPN_Server_via_Windows_PC)
- [封面圖片來源](https://www.ghibli.jp/info/013772/?ref=seanmars.dev)
