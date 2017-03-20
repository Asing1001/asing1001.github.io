---
title: 三種色彩表達法 - RGB & HEX & ColorName
date: 2014-11-12 20:33:00
tags: [CSS]
---

小弟在剛開始寫程式的時候，看到顏色就一陣頭痛，懶惰如我終於受不了決定來研究解藥了。

常見分為<span style="color:#F00">Color Name</span>、<span style="color:#0F0">HEX</span>、<span style="color:#00F">RGB</span>三種表達方式：


## ColorName, 直接打顏色名稱：
如：Black、White等140種顏色，就不多做介紹，詳細請參考：[ColorName顏色列表](http://www.w3schools.com/html/html_colornames.asp)  



## HEX, 十六進位制(hexadecimal)：
[HEX色彩查詢 http://www.color-hex.com/](http://www.color-hex.com/)

數字兩兩一組，前面兩個數字代表Red,中間兩個是Green，最後則是Blue，0是最小值沒有顏色，因此#000000是黑色；F則是十六進位最大值，因此#FFFFFF所有顏色達到最大值會變成白色。

簡寫方式：若每組兩兩相同則可以合併，讓6碼變成3碼，如下：

<div style="color: black;">#000 黑色</div>

<div style="color: red;">#F00 紅色</div>

<div style="color: lime;">#0F0 綠色</div>

<div style="color: blue;">#00F 藍色</div>

<div style="background: #000; color: white;">#FFF 白色</div>

<div style="color: #888888;">#888 灰色  </div>



## RGB(Red Green Blue)：
[RGB表](http://www.rapidtables.com/web/color/RGB_Color.htm)
採十進位，最小值為0，最大為256
<div style="color: black;">rgb(0,0,0) 黑色</div>

<div style="color: rgb(256,0,0);">rgb(255,0,0) 紅色</div>

<div style="color: lime;">rgb(0,255,0) 綠色</div>

<div style="color: blue;">rgb(0,0,255) 藍色</div>

<div style="background: #000; color: white;">rgb(255,255,255) 白色</div>

<div style="color: #888888;">rgb(136,136,136) 灰色  </div>

