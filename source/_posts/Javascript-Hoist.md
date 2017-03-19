title: |
	Javascript Hoist
date: 2014-10-28 21:38:00
tags: [JavaScript]
---

[W3School Hoist解說參考](http://www.w3schools.com/js/js_hoisting.asp)  
大家可能沒想過，為什麼在JavaScript中我們能在前面就叫用後來宣告的方法呢？  
這是因為JavaScript中"Hoist"這個行為所產生的結果，今天就來和大家分享這個小知識吧！  

"Hoist"中文翻做"提升"，顧名思義，就是在Javascript中預設會自動將宣告的變數/方法提到最前面，因此先使用後來才宣告變數/方法是沒問題的，如下：

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;"><a name="more"></a></div>

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14px;">x = </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-size: 14px;">5</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14px;">; </span><span style="color: green; font-family: Consolas, 'courier new'; font-size: 14px;">// </span><span style="color: green; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">指定 x = 5</span></div>

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14px;">elem = document.getElementById(</span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-size: 14px;">"demo"</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14px;">); </span><span style="color: green; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">// 找到id=demo的標籤物件</span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14px;">elem.innerHTML = x; </span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14px; text-align: -webkit-auto;">                    </span></div>

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="color: brown; font-family: Consolas, 'courier new'; font-size: 14px;">var</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14px;"> x; </span><span style="color: green; font-family: Consolas, 'courier new'; font-size: 14px;">// Declare x</span></div>

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="color: green; font-family: Consolas, 'courier new'; font-size: 14px;">  
</span></div>

這和下面結果是一樣的：

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="font-family: Consolas, 'courier new'; font-size: 14px;">  
</span></div>

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="color: brown; font-family: Consolas, 'courier new'; font-size: 14px;">var</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14px;"> x; </span><span style="color: green; font-family: Consolas, 'courier new'; font-size: 14px;">// Declare x</span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14px;">x = </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-size: 14px;">5</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14px;">; </span><span style="color: green; font-family: Consolas, 'courier new'; font-size: 14px;">// 指定 x = 5</span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14px;">elem = document.getElementById(</span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-size: 14px;">"demo"</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14px;">); </span><span style="color: green; font-family: Consolas, 'courier new'; font-size: 14px;">// 找到id=demo的標籤物件</span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14px;">elem.innerHTML = x;</span></div>

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14px;">  
</span></div>

但Hoist這個行為常常被忽略，因此會造成意想不到的BUG。  
舉例來說，通常宣告變數是在方程式前宣告，但前面卻不小心指定過了：

<div style="orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="text-align: -webkit-auto;"></span>  
(function() {  
x = 5; //這裡不小心用了x  
})()<span style="text-align: -webkit-auto;">

<div style="text-align: -webkit-auto;"><span style="font-family: Consolas, courier new;"><span style="font-size: 14.3999996185303px;">.</span></span></div>

<div style="text-align: -webkit-auto;"><span style="font-family: Consolas, courier new;"><span style="font-size: 14.3999996185303px;">.</span></span></div>

</span>

<div style="text-align: -webkit-auto;"><span style="text-align: -webkit-auto;"><span style="font-family: Consolas, courier new;"><span style="font-size: 14.3999996185303px;">.</span></span></span>隔了很長的程式碼</div>

<span style="text-align: -webkit-auto;">

<div style="text-align: -webkit-auto;"><span style="font-family: Consolas, courier new;"><span style="font-size: 14.3999996185303px;">.</span></span></div>

<div style="text-align: -webkit-auto;"><span style="font-family: Consolas, courier new;"><span style="font-size: 14.3999996185303px;">.</span></span></div>

</span>var x = 123;  
(function() {  
x++;  
})()<span style="text-align: -webkit-auto;">

<div style="text-align: -webkit-auto;">結果x預期出來是124，結果實際上發現只有6.... </div>

</span>  
可以看到在後面無意間改變了前面變數的值，造成找很久都找不出來的BUG，因此最好的解決方式是：</div>

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="font-family: Consolas, 'courier new'; font-size: 14px;">  
</span></div>

<div style="font-family: Tahoma; font-size: 19px; orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="font-family: Consolas, 'courier new';">**永遠宣告變數在最上方！**</span></div>