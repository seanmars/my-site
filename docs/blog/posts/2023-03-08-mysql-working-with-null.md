---
title: Working with NULL Values on MySQL
tags: database, mysql, null
---

# Working with NULL Values on MySQL

今天在操作 MySQL 的時候剛好遇到新增的欄位資料都是 `NULL` 造成程式會因此有些問題，所以就想把已存在的 row 該欄位是 `NULL` 的都填上資料。

本來的 schema 是長這樣:
idnameskill1abc12def13ghy4
後來新增加一欄 `level`
idnameskilllevel1abc1NULL2def1NULL3ghy4NULL
所以就想說直接先都把 `level` 設為 1，所以直接下了下面這個指令

    UPDATE `role` SET level = 1 WHERE level = NULL;
    

結果什麼都沒更新到...，後來 google 了一番，原來 `NULL` 是特別的存在，官方表示 `NULL means “a missing unknown value”`，如果要對 `NULL` 做判斷要用 `IS NULL` or `IS NOT NULL`；所以正確的語法應該要用這樣:

    UPDATE `role` SET level = 1 WHERE level IS NULL;
    

最後終於搞定啦!

參考:

- [Selecting All Data](https://dev.mysql.com/doc/refman/8.0/en/selecting-all.html)
- [Working with NULL Values](https://dev.mysql.com/doc/refman/8.0/en/working-with-null.html)
- [MYSQL syntax not evaluating not equal to in presence of NULL](https://stackoverflow.com/questions/16186674/mysql-syntax-not-evaluating-not-equal-to-in-presence-of-null/16186688#16186688)
- [What is this operator <=> in MySQL?](https://stackoverflow.com/questions/21927117/what-is-this-operator-in-mysql/21928508#21928508)
- 封面圖來源: [ghibli.jp](https://www.ghibli.jp/info/013409/)
