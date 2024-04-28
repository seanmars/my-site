---
title: Memo for MySQL
---

# Memo for MySQL

- 列出某 schema 中的所有 Index

    SELECT
        DISTINCT TABLE_NAME,
        INDEX_NAME
    FROM
        INFORMATION_SCHEMA.STATISTICS
    WHERE
        TABLE_SCHEMA = '{schema}' AND INDEX_NAME != 'PRIMARY';
    

參考:

- 封面圖來源: [ghibli.jp](https://www.ghibli.jp/info/013409/)
