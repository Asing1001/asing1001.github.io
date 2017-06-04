---
title: 如何在關閉Outlook後自動隱藏至右下角?
date: 2014-11-08 23:16:00
tags: [實用工具]
---

在公司使用Outlook時常常不小心按到X，Outlook就直接關掉了，這時候收到信就不會自動通知...，上網找到了按關閉時收到右下角工具列以及縮小時自動隱藏到右下角的方法，在此分享給各位^^
<!-- more -->

## 縮小時自動隱藏到右下角工具列

開啟Outlook後→右下角工具列找到outlook圖示→右鍵→縮小時自動隱藏(Hide When Minimized)

[![](https://4.bp.blogspot.com/-KiyveuDpwXw/VFnL7ydlo1I/AAAAAAAAJXU/pp1Umg6JtK0/s320/1b6a954ee74d809c9ba845a49b557c0a-754712.jpeg)](https://4.bp.blogspot.com/-KiyveuDpwXw/VFnL7ydlo1I/AAAAAAAAJXU/pp1Umg6JtK0/s1600/1b6a954ee74d809c9ba845a49b557c0a-754712.jpeg)

## 按關閉時隱藏到右下角  
1. 安裝 Microsoft Visual C++ 2010 SP1 Redistributable Package 32-bit and 64-bit (both required for x64 Windows)
[https://www.microsoft.com/en-us/download/details.aspx?id=5555](https://www.microsoft.com/en-us/download/details.aspx?id=5555)
(這是讓下一步的增益集能正常運作)

2. 至下面連結下載 KeepOutlookRunning.dll ，依電腦選擇64位元或32位元的(不知道的話就先都下載)。
[https://sourceforge.net/projects/keepoutlook/files/0.0.1/](https://sourceforge.net/projects/keepoutlook/files/0.0.1/)

3. 至你的OUTLOOK.EXE放的位置( 我的是 C:\Program Files (x86)\Microsoft Office\Office12 ) →右鍵→使用系統管理員身分執行

4. 我想是因為有兩種不同版本，因此有兩種不一樣的路徑，提供給各位：
   1. 工具→信任中心→增益集  (我的2007版本是這個)
   2. 檔案→選項→增益集

      ![](https://4.bp.blogspot.com/-7tsXJ0-UfK0/VFnL8l7SYdI/AAAAAAAAJXg/enhKYUjiNf0/s1600/7ad883e297eae239c6784893423ddbfd-758348.jpeg)

5. 最下方進入(圖中最下方的GO)→加入→選擇剛剛下載的DLL→OK

   [![](https://2.bp.blogspot.com/-o-fPVYy1aXg/VFnL9FX6nhI/AAAAAAAAJXs/C5zMrEAKU60/s320/95cd4f95d5bf27cedd8632c25c3ffc1c-760630.jpeg)](https://2.bp.blogspot.com/-o-fPVYy1aXg/VFnL9FX6nhI/AAAAAAAAJXs/C5zMrEAKU60/s1600/95cd4f95d5bf27cedd8632c25c3ffc1c-760630.jpeg)

   [![](https://3.bp.blogspot.com/-bntxwvx2LiI/VFnL9zfUWQI/AAAAAAAAJX4/oIuJkMxhKRM/s320/3ef837ba78f8f19934b1a73f20438a43-763517.jpeg)](https://3.bp.blogspot.com/-bntxwvx2LiI/VFnL9zfUWQI/AAAAAAAAJX4/oIuJkMxhKRM/s1600/3ef837ba78f8f19934b1a73f20438a43-763517.jpeg)

6. 重新啟動Outlook會發現按關閉時自動跳到右下角狀態列了！

**常見問題：**

按加入後出現錯誤
`Not loaded. Certificate of signed and load at startup COM Add-in is not in trusted source list.`  
解決方法是取消勾選 `"apply macro security settings to installed add-ins".` 這個選項(中文我不太確定，如圖)

[![](https://4.bp.blogspot.com/-bldRZ40hl0k/VFnL-cC7tiI/AAAAAAAAJYE/BS6tdEtzqWg/s320/d696326a00fa258ca15dda058f5700de-765879.jpeg)](https://4.bp.blogspot.com/-bldRZ40hl0k/VFnL-cC7tiI/AAAAAAAAJYE/BS6tdEtzqWg/s1600/d696326a00fa258ca15dda058f5700de-765879.jpeg)

