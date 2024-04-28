---
title: 指令大全
tags: cli, windows, linux
---

# 指令大全

收集一些常用或者好用的指令

## Windows PowerShell

    # 查詢所有 listening 狀態的 port 與執行檔名稱
    netstat -natb
    
    # 更快速找到 listening 狀態的 port 與執行檔名稱
    Get-NetTCPConnection -State Listen -LocalPort {Port}
    
    # Ping host with port
    Test-Connection www.local.dev -Detail -TcpPort 22
    

## Bash/Zsh
