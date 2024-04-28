---
title: Node.js PDF 轉 Base64 後會變空白的問題
---

# Node.js PDF 轉 Base64 後會變空白的問題

幫朋友解決寄信附件 PDF 空白的問題，在 Node.js 中產生 PDF 檔案後如果用 [fs](https://nodejs.org/api/fs.html) 讀檔後再丟到 [Buffer](https://nodejs.org/api/buffer.html) 會造成 PDF 變空白的狀況。

    const filepath = '/file.pdf';
    const pdfBinary = fs.readFileSync(filepath, 'base64');
    const pdfData = Buffer.from(pdfBinary, 'base64');
    const base64Pdf = pdfData.toString('base64');
    

問題就在 `fs.readFileSync(filepath, 'base64')`，

要把 `encode` 改成 `null`，`Buffer.from(pdfBinary, 'base64')` 時才不會造成二次轉換。

完整的 code 如下

    const filepath = '/file.pdf';
    const pdfBinary = fs.readFileSync(filepath, null);
    const pdfData = Buffer.from(pdfBinary, 'base64');
    const base64Pdf = pdfData.toString('base64');
    

參考:

- 封面圖來源: [ghibli.jp](https://www.ghibli.jp/info/013409/?ref=seanmars.dev)
