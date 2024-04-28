---
title: 解決在 Ubuntu 22.04 上安裝 Ghost 遇到的問題
tags: ubuntu, ghost, error
---

# 解決在 Ubuntu 22.04 上安裝 Ghost 遇到的問題

這次自己在安裝 Ghost CMS 的時候照著官方指引遇到了一些問題，留個記錄。

照著 [Ghost 官方教學](https://ghost.org/docs/install/ubuntu/) 應該會遇到一些狀況；

首先遇到底下這個錯誤

    ✖ Starting Ghost
    One or more errors occurred.
    
    1) CliError
    
    Message: Error trying to connect to the MySQL database.
    Help: You can run `ghost config` to re-enter the correct credentials. Alternatively you can run `ghost setup` again.
    
    
    2) GhostError
    
    Message: Ghost was able to start, but errored during boot with: Access denied for user 'root'@'localhost'
    Help: Unknown database error
    Suggestion: journalctl -u ghost_localhost -n 50
    
    Debug Information:
        OS: Ubuntu, v22.04.1 LTS
        Node Version: v16.17.0
        Ghost Version: 5.15.0
        Ghost-CLI Version: 1.23.0
        Environment: production
        Command: 'ghost setup'
    

這個錯誤是因為 MySQL 安裝後沒有設定 root 的密碼造成的，所以需要使用 `sudo mysql -u root` 來設定密碼。

    mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password by 'the-new-password';
    

這邊若你密碼設定不符合安全應該會遇到底下此錯誤

    ERROR 1819 (HY000): Your password does not satisfy the current policy requirements
    

可以藉由以下指令來確認 MySQL 密碼強度驗證相關資訊

    mysql> SHOW VARIABLES LIKE 'validate_password%';
    

最後照著密碼強度的規則重新設置一個密碼後再次 `ghost setup` 來設置 MySQL 相關資訊即可。
