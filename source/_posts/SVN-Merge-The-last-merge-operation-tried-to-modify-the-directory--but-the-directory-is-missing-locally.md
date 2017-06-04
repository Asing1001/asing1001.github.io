---
title: SVN Merge - The last merge operation tried to modify the directory , but the directory is missing locally.
date: 2014-11-17 20:47:00
tags: [Trouble Shooting, SVN]
---

今天在SVN上做Merge動作時，發生Tree Conflict錯誤：  
[![](https://4.bp.blogspot.com/-_K8-99BVPvw/VGntsYeN3HI/AAAAAAAAJZw/CWShaTTkGak/s1600/tree%2Bconflict.png)](https://4.bp.blogspot.com/-_K8-99BVPvw/VGntsYeN3HI/AAAAAAAAJZw/CWShaTTkGak/s1600/tree%2Bconflict.png)
<!-- more -->

雙擊點開顯示：
`the last merge operation tried to modify the directory , but the directory is missing locally.`


[![](https://2.bp.blogspot.com/-mcXzGkies6s/VGntxvCtRKI/AAAAAAAAJZ4/0o9JBnyUbJM/s1600/error.png)](https://2.bp.blogspot.com/-mcXzGkies6s/VGntxvCtRKI/AAAAAAAAJZ4/0o9JBnyUbJM/s1600/error.png)

嘗試過使用上圖介面中的每個按鍵來解決，並且上網查了很多資料，都沒有用.....

只好自己摸索了一番，最後發現是在Merge時的兩個目錄不同所導致的。  
也就是 "URL to Merge from" 和 "Working Copy" 應該要處於SVN中的同一層！而我不小心多進入了directory這個資料夾，導致雖然選的Revision是對的，卻造成Tree Conflict。

[![](https://2.bp.blogspot.com/-4PW4Q60CJDw/VGntxuhOmOI/AAAAAAAAJZ8/uDwaDfwX6eI/s1600/2014-11-17%2B16_35_24-star2.jpg)](https://2.bp.blogspot.com/-4PW4Q60CJDw/VGntxuhOmOI/AAAAAAAAJZ8/uDwaDfwX6eI/s1600/2014-11-17%2B16_35_24-star2.jpg)

所以解決方式是**把URL to Merge from和Working Copy的都選在同一層**就解決了！

紀錄下來希望能幫助到遇到同樣問題的人：)