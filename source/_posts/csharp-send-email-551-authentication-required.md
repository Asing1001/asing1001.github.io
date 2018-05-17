---
title: Gmail sending error 5.5.1 Authentication Required.
date: 2017-03-24 00:10:55
tags: [C#, Trouble Shooting, Google]
---

## 錯誤
程式自動寄送Email時發生錯誤：
`SMTP 伺服器需要安全連接，或用戶端未經驗證。伺服器回應為: 5.5.1 Authentication Required.`
<!-- more -->

## 原因
Gmail權限預設不讓不明程式發送EMAIL，需到Google設定自己的電子郵件允許一般應用程式使用

## 解決方法
登入Google→至[Google帳號設定頁面](https://myaccount.google.com/security)→已連結的網站與應用程式->允許安全性較低的應用程式→啟用
{% asset_img "setting-location.jpg" %}

## 程式碼參考
[C# SMTP Sending Email](/2014/11/02/CSharp-SMTP-Email/)