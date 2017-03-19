---
title: 如何計算兩日期區間有無重疊？
date: 2017-01-17 22:21:00
tags: [Algorithm]
---

今天剛好遇到要計算兩個日期區間有沒有重疊，發現這個問題其實可以想成，A和B一生中有沒有可能相遇？  

這麼一想就簡單多了，就是兩人必須在對方死亡前出生！

``` javascript
var isOverlap = a.start < b.end && b.start < a.end
```