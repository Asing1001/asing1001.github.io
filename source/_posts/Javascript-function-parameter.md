title: |
	Javascript function 的參數傳遞 [ function parameter ]
date: 2014-11-05 16:30:00
tags: [JavaScript]
---

有寫過C#或JAVA的朋友一開始接觸 Javascript 是否和我一樣，覺得 Javascript funtion 傳遞的參數很奇怪呢？小弟困擾了很久，決定上w3school研讀一番，根據自己的理解整理如下：  
**<span style="font-size: large;"></span>**  
<a name="more"></a>**<span style="font-size: large;">參數規則(一) 不用傳剛剛好的參數給function</span>**  

<div>假設現在有一個 function myfunc(x,y,z){ ....... }當我們使用 myfunc(1,2) 呼叫時，傳的參數不夠多，和C#、Java不一樣，不會出現exception！<span style="background-color: white;">且</span><span style="background-color: yellow;">第三個參數會自動視為"undefined"</span>，可以想像是一個function就有「多載」的感覺！但畢竟這不是多載，最好還是給會出現undefined的參數一個初始值，如下：  

<pre class="Javascript" name="code">function myfunc(x,y,z){  
    if (z === undefined) {  
        z = 0;  
    }   
}</pre>

<div style="font-family: Tahoma; orphans: 2; text-align: -webkit-auto; widows: 2;">順帶一提，內容改為 z<span style="background-color: white; font-family: Consolas, 'courier new';"> = z || </span><span style="color: mediumblue; font-family: Consolas, 'courier new';">0</span><span style="background-color: white; font-family: Consolas, 'courier new';">; 也有一樣的效果：</span></div>

<pre class="Javascript" name="code">function myfunc(x,y,z){   
     z = z || 0;  
}  
</pre>

看到這裡，或許會和我一樣有個疑惑，<span style="background-color: yellow;">傳四個參數會怎麼樣呢？</span>  
例如：myfunc(1,2,3,4)  

結果是Javascript一樣不會出現exception，只是<span style="background-color: yellow;">第四個參數會自動忽略掉</span>！  
個人認為這是好處也是壞處，寫的時候不太會有exception，但有Bug也找不太出來......  
**<span style="font-size: large;">  
</span>****<span id="arguments" style="font-size: large;">參數規則(二) 內建的 Arguments Object</span>**  
請先停下來思考看看以下程式能執行嗎？</div>

<div>

<pre class="C#" name="code">x = findMax(1, 123, 500, 115, 44, 88);  
function findMax() {  
    var i, max = 0;  
    for (i = 0; i < arguments.length; i++) {  
        if (arguments[i] > max) {  
            max = arguments[i];  
        }  
    }  
    return max;  
}  
</pre>

**可以的！**相信對Javascript的初學者來說，會覺得  
1.arguments未宣告  
2.依照規則一，參數傳太多會全部忽略！  
3.執行後結果=0  

但是實際執行結果是最大的 500 !  
很驚訝嗎？這是很常見的Javascript語法喔！  

這裡我們從解釋arguments從哪來的，讓大家知道這為甚麼跑得過。[上一篇](http://sincode.blogspot.tw/2014/10/javascript-this-function.html)有提到，function是一個物件，而arguments呢則是一個function的內建屬性，可以想像成一個class裡面有一個list的感覺！而<span style="background-color: yellow;">當傳參數給function後，funtion會依照你的參數，以逗號區隔，一個個存入內建叫做arguments的陣列中</span>，正因此我們可以直接使用arguments來操作參數，而不需要在function宣告設一整串參數，也解決了function參數不能指定特定型別，如"Array"的問題！  

現在再看一次這個function，是不是豁然開朗了呢？</div>

<pre class="C#" name="code">function findMax() {  
    var i, max = 0;  
    for (i = 0; i < arguments.length; i++) {  
        if (arguments[i] > max) {  
            max = arguments[i];  
        }  
    }  
    return max;  
}</pre>