---
title: 如何找 Windows cmd 輸入的 command 實體路徑？
date: 2016-08-08 11:11:00
tags: [cmd]
---

語法：`Where + Command`
範例：`where node`
輸出：`C:\Program Files\nodejs\node.exe`

![](https://1.bp.blogspot.com/-tG05YUpw3iA/V6f3QccmC3I/AAAAAAAAO5o/OeKMYhdXrBQ-4OOm8Hw1aFrMPBX2sFYLQCK4B/s640/Administrator_%2BWindows%2BCommand%2BProcessor-000103.jpg)

會特別找這個是因為我常更新某個command後，卻發現版本依然停在舊的，這時候用where就知道大概是哪個環境變數和舊版程式在搞鬼囉！