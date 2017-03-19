title: |
	JavaScript 封裝 [JavaScript Closure]
date: 2014-10-29 23:30:00
tags: [JavaScript]
---

<div style="orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="font-family: Consolas, 'courier new'; font-size: 14.3999996185303px; text-align: -webkit-auto;">  
</span></div>

今天要介紹的是Javascript裡非常重要的概念 - "封裝(Closure)"  
也就是和C#、JAVA等語言一樣，變數也會有Private、Public的差別！  

<a name="more"></a>  

先介紹 global variable(全域變數)和 local variable(私有變數)的差別：  

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;">

*   <span style="color: #404040; font-family: verdana, helvetica, arial, sans-serif;"><span style="font-size: 14px;">**global**<span style="background-color: white; font-size: 14.3999996185303px;"> variable  
    直接宣告並隸屬於window物件的變數  
    <span style="color: brown; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">var</span><span style="color: black; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;"> a = </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">4</span><span style="color: black; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">;</span>  
    <span style="color: brown; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">function</span><span style="color: black; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;"> myFunction() {</span>  
    <span style="color: black; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">    </span><span style="color: brown; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">return</span><span style="color: black; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;"> a * a;</span>  
    <span style="color: black; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">}</span></span></span></span>
*   <span style="color: #404040; font-family: verdana, helvetica, arial, sans-serif;"><span style="font-size: 14px;"><span style="background-color: white; font-size: 14.3999996185303px;">**local**<span style="font-size: 14.3999996185303px;"> variable  
    宣告在function內的變數  
    <span style="color: brown; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">function</span><span style="color: black; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;"> myFunction() {</span>  
    <span style="color: black; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">    </span><span style="color: brown; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">var</span><span style="color: black; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;"> a = </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">4</span><span style="color: black; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">;</span>  
    <span style="color: black; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">    </span><span style="color: brown; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">return</span><span style="color: black; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;"> a * a;</span>  
    <span style="color: black; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">}</span></span></span></span></span>

</div>

這樣的方程式在合作開發時，由於其他人不知道你有設哪些變數，常常會造成變數衝突問題，如下：  

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;"><span style="color: brown;">var</span></span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;"> counter = </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">0</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">;</span></div>

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="color: brown; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">function</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;"> yourfunction() {</span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">    counter <span style="color: mediumblue;">=5</span></span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">;</span></div>

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">    //do something....</span></div>

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">}</span>  

<span style="font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;"><span style="color: brown;">var</span></span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;"> counter = <span style="color: mediumblue;">10</span></span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">;</span>  

<span style="color: brown; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">function</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;"> othersfunc() {</span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">    counter += </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">1</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">;</span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">}</span>  

<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">add();</span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">add();</span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">add();</span>  
<span style="color: green; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">// the counter is now equal to 13</span></div>

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="color: green; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">  
</span></div>

尤其是大型專案很多JS檔，更容易發生錯誤，所以只好把全域變數變為私有變數：  

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="font-family: Consolas, courier new;"><span style="font-size: 14px;">  
</span></span></div>

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="color: brown; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">function</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;"> add() {</span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">    </span><span style="color: brown; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">var</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;"> counter = </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">0</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">;</span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">    counter += </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">1</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">;</span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">}</span>  

<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">add();</span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">add();</span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">add();</span>  

<span style="color: green; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">// the counter should now be 3, but it does not work !</span></div>

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="color: green; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">  
</span></div>

很明顯的，這樣一來每次call這個function時，counter又再次被設為0，所以這樣也行不通！  
因此就要使用inner function了：  

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">  
</span></div>

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="color: brown; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">function</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;"> add() {</span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">    </span><span style="color: brown; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">var</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;"> counter = </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">0</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">;</span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">    </span><span style="color: brown; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">function</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;"> plus() {counter += </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">1</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">;}</span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">    plus();    </span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">    </span><span style="color: brown; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">return</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;"> counter; </span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">}</span></div>

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">  
</span></div>

這樣一來counter就變為私有變數了，然而這樣要怎麼"呼叫"函式又變成另外一個問題，因此我們要用"closure"(封裝)來解決這個難題：  

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="font-family: Consolas, courier new;"><span style="font-size: 14px;">  
</span></span></div>

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="color: brown; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">var</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;"> add = (</span><span style="color: brown; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">function</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;"> () {</span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">    </span><span style="color: brown; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">var</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;"> counter = </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">0</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">;</span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">    </span><span style="color: brown; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">return</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;"> </span><span style="color: brown; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">function</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;"> () {return counter += </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">1</span><span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">;}</span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">})();</span>  

<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">add();</span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">add();</span>  
<span style="background-color: white; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">add();</span>  

<span style="color: green; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">// the counter is now 3</span></div>

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;"><span style="color: green; font-family: Consolas, 'courier new'; font-size: 14.3999996185303px;">  
</span></div>

解釋：可以看到帶有()的自發性函式只會執行一次，並且設定私有變數counter為0，再return一個function給var add這個object，這時候就達到counter只設定一次，add也變成function () {return counter += 1;}的目的了！  

<div>  
再明確講一次封裝重點要件：  

<div style="orphans: 2; text-align: -webkit-auto; widows: 2;">

1.  <span style="font-family: Consolas, courier new;"><span style="background-color: white; font-size: 14.3999996185303px;">自發執行函數 (function(){ //do something  })()</span></span>
2.  <span style="font-family: Consolas, courier new;"><span style="background-color: white; font-size: 14.3999996185303px;">在上述函數內宣告私有變數 var counter = 0;</span></span>
3.  <span style="font-family: Consolas, courier new;"><span style="background-color: white; font-size: 14.3999996185303px;">return function(){} 給指定物件 var add</span></span>
4.  <span style="font-family: Consolas, courier new;"><span style="background-color: white; font-size: 14.3999996185303px;">完工！</span></span>

</div>

感想：發明的人真厲害，很聰明的做法...！</div>