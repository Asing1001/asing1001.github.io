---
title: Javascript Hoist
date: 2014-10-28 21:38:00
tags: [JavaScript]
---

[W3School Hoist解說參考](http://www.w3schools.com/js/js_hoisting.asp)  
為什麼在JavaScript中我們能在檔案最前面叫用後來宣告的方法，就是因為JavaScript中"Hoist"這個行為所產生的結果！

"Hoist"中文翻做"提升"，顧名思義，就是在Javascript中預設會自動將宣告的變數/方法提到最前面，因此先使用後來才宣告變數/方法是沒問題的，如下：
```Javascript
x = 5; // 指定 x = 5
elem = document.getElementById("demo"); // 找到id=demo的標籤物件
elem.innerHTML = x;                     
var x; // Declare x
```
這和下面結果是一樣的：
```Javascript
var x; // Declare x
x = 5; // 指定 x = 5
elem = document.getElementById("demo"); // 找到id=demo的標籤物件
elem.innerHTML = x;
```

但Hoist這個行為常常被忽略，因此會造成意想不到的BUG。
舉例來說，通常宣告變數是在方程式前宣告，但前面卻不小心指定過了：
```Javascript
(function() {
x = 5; //這裡不小心用了x
})()
//隔了很長的程式碼....
//...
//...
var x = 123; 
(function() { 
x++; 
})()
```
結果x預期出來是124，結果實際上發現只有6.... 

可以看到在後面無意間改變了前面變數的值，造成找很久都找不出來的BUG，因此最好的解決方式是：

永遠宣告變數在最上方！