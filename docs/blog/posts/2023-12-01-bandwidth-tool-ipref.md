---
title: 網路效能測試工具 iPref
tags: ipref, bandwidth, tool
---

# 網路效能測試工具 iPref

今天在 Discord 看到網友介紹了一套不錯的網路效能測試工具 [iPref](https://iperf.fr/)，之前都只有關心對外網路的狀況大概就是用 [SpeedTest](https://www.speedtest.net/) 或是 [Fast](https://fast.com/) 測試家中網路的速度，都沒關心過內網端對端的效能如何。

[iPref](https://iperf.fr/) 這款工具，就是可以測試端到端的網路效能，以下是 [wiki](https://www.wikiwand.com/zh-tw/Iperf) 的介紹：

    iPref 是一個廣泛使用的網路性能測量和調整工具。它的意義在於它是一個跨平台的工具，可以為任何網路提供標準化的性能測量。iPref 具有客戶端和伺服器功能，可以創建數據流來測量兩端之間單向或雙向的網絡吞吐量。典型的 iPref 輸出包含一個有時間標記的數據傳輸量和吞吐量測量的報告。
    

基本的使用方式就是先在一端建立起 server 另一端使用 client mode 來連到 server 測試速度。

A 設備: 192.168.1.1

    ipref3 -s
    

Output:

    -----------------------------------------------------------
    Server listening on 5201
    -----------------------------------------------------------
    

B 設備: 192.168.1.2

    ipref3 -c 192.168.1.1
    

Output:

    Connecting to host 192.168.1.1, port 5201
    [  4] local 192.168.1.2 port 62406 connected to 192.168.1.1 port 5201
    [ ID] Interval           Transfer     Bandwidth
    [  4]   0.00-1.01   sec  96.6 MBytes   804 Mbits/sec
    [  4]   1.01-2.01   sec  82.2 MBytes   691 Mbits/sec
    [  4]   2.01-3.00   sec  90.8 MBytes   764 Mbits/sec
    [  4]   3.00-4.00   sec  94.9 MBytes   797 Mbits/sec
    [  4]   4.00-5.01   sec   132 MBytes  1.10 Gbits/sec
    [  4]   5.01-6.01   sec   106 MBytes   886 Mbits/sec
    [  4]   6.01-7.00   sec  96.0 MBytes   808 Mbits/sec
    [  4]   7.00-8.01   sec   131 MBytes  1.09 Gbits/sec
    [  4]   8.01-9.00   sec   169 MBytes  1.42 Gbits/sec
    [  4]   9.00-10.00  sec  98.1 MBytes   826 Mbits/sec
    - - - - - - - - - - - - - - - - - - - - - - - - -
    [ ID] Interval           Transfer     Bandwidth
    [  4]   0.00-10.00  sec  1.07 GBytes   919 Mbits/sec                  sender
    [  4]   0.00-10.00  sec  1.07 GBytes   919 Mbits/sec                  receiver
    

參考:

- [Wiki](https://www.wikiwand.com/zh-tw/Iperf)
- 封面圖來源: [ghibli.jp](https://www.ghibli.jp/info/013409/)
