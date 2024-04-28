---
title: Port forwarding on Windows
---

# Port forwarding on Windows

最近因為 Docker Desktop on Windows 的許可證關係導致需要找替代品，目前覺得還堪用的就是 [Podman](https://podman.io/) 了，因此就開始了轉換之路。

目前 [Podman](https://podman.io/) 已經越來越完善了，所以基本上算是無痛轉移，除了 port 轉發這件事情，不知道為啥沒有處理，所以研究了一下如何使用 Windows 內建的工具 [Netsh](https://learn.microsoft.com/zh-tw/windows-server/networking/technologies/netsh/netsh-contexts) 來達到轉發的功能。

基本上只要使用以下指令就可以達到效果，還蠻簡單的：

    netsh interface portproxy add v4tov4 listenport=8080 listenaddress=0.0.0.0 connectport=8080 connectaddress=127.0.0.1
    

不過中間遇到了一些問題，因為網路上找了不少資料 `connectaddress` 的值都是填寫 `podman 的 wsl` 的 IP，但不知道為啥我使用後都沒效果，後來看到有些人說直接填 `127.0.0.1` 即可，試了一下果然就通了。

另外 `netsh` 的指令需要使用管理者權限才可以執行。

以下提供一個直接抓取所有 container port 然後設定所有 port 轉發的 PowerShell script：

    
    # This script is used to forward ports from Windows to WSL2
    
    # Usage:
    # 1. Open PowerShell as an administrator
    # 2. Run the following command:
    #    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
    # 3. Run the following command:
    #    .\port-forwarding.ps1 [-TargetAddress your.connect.ip.address]
    # 4. Run the following command to check the port forwarding:
    #    netsh interface portproxy show v4tov4 all
    
    param (
        [string]$TargetAddress
    )
    
    # Check if the script is running as an administrator
    if (-NOT ([Security.Principal.WindowsPrincipal][Security.Principal.WindowsIdentity]::GetCurrent()).IsInRole([Security.Principal.WindowsBuiltInRole]::Administrator)) {
        Write-Host "This script requires administrator privileges. Please run the script as an administrator."
        Exit 1
    }
    
    # Check if the $TargetAddress parameter is provided
    if (-not $TargetAddress) {
        $TargetAddress = $(wsl hostname -I)
    }
    
    $ports = podman ps -a --format "table {{.Ports}}" | ForEach-Object { $_.Split(':')[1]?.Split('-')?[0] }
    foreach ($port in $ports) {
        if($port -eq $null) {
            continue
        }
        
        $command = "netsh interface portproxy add v4tov4 listenport=$port listenaddress=0.0.0.0 connectport=$port connectaddress=$TargetAddress"
        Invoke-Expression $command
        Write-Host "netsh port: $($port)"
    }
    
    netsh interface portproxy show v4tov4 all
    

參考:

- 封面圖來源: [ghibli.jp](https://www.ghibli.jp/info/013409/)
