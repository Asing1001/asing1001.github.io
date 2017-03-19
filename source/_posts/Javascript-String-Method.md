title: |
	Javascript String 相關方法 [Javascript String Method]
date: 2014-10-28 00:27:00
tags: [JavaScript]
---

<div>

*   <span style="background-color: white; color: #404040; font-size: 14px;">**<span style="font-family: Verdana, sans-serif;">indexOf() 搜尋第一個符合的字，回傳index，若無則回傳-1  
    <span style="color: brown; font-weight: normal;">var</span><span style="color: black; font-weight: normal;"> str = </span><span style="color: mediumblue; font-weight: normal;">"Please locate where 'locate' occurs!"</span><span style="color: black; font-weight: normal;">;</span>  
    <span style="color: brown; font-weight: normal;">var</span><span style="color: black; font-weight: normal;"> pos = str.indexOf(</span><span style="color: mediumblue; font-weight: normal;">"locate"</span><span style="color: black; font-weight: normal;">);</span></span>**</span>

*   <span style="font-family: Verdana, sans-serif;"><span style="background-color: white; color: #404040; font-size: 14px;">**lastIndexOf() **</span>**搜尋最後一個符合的字，回傳index，****若無則回傳-1**</span>

*   ****<span style="font-family: Verdana, sans-serif;">search() 和 indexOf() 完全一樣<a name="more"></a></span>****

*   **<span style="font-family: Verdana, sans-serif;"><span style="color: #404040;">slice(start,end) 切出start~end的字串並回傳</span></span>**

    <div>****<span style="font-family: Verdana, sans-serif;">******<span style="color: brown; font-weight: normal;">var</span><span style="color: black; font-weight: normal;"> str = </span><span style="color: mediumblue; font-weight: normal;">"Apple, Banana, Kiwi"</span><span style="color: black; font-weight: normal;">;</span>  
    <span style="color: brown; font-weight: normal;">var</span><span style="color: black; font-weight: normal;"> res = str.slice(</span><span style="color: mediumblue; font-weight: normal;">7</span><span style="color: black; font-weight: normal;">,</span><span style="color: mediumblue; font-weight: normal;">13</span><span style="color: black; font-weight: normal;">);  
    res 的結果為 </span>************<span style="font-weight: normal;"><span style="color: mediumblue;">Banana</span>  
    若start,end為負數也可以！  
    從後面倒數，最後一個字當作0，從後面切回來！</span>******</span>****</div>

    <div><span style="font-family: Verdana, sans-serif;">******<span style="color: mediumblue; font-weight: normal;"><span style="color: brown;">var</span><span style="color: black;"> res = str.slice(</span>-12<span style="color: black;">,</span>-6<span style="color: black;">);  
    res 結果依然是 </span></span>****************<span style="font-weight: normal;"><span style="color: mediumblue;">Banana</span>  

    若不傳end參數，則切到最 後面 並回傳回來  
    <span style="color: brown;">var</span> res = str.slice(<span style="color: mediumblue;">7</span>);<span style="color: brown;">var</span> res = str.slice(<span style="color: mediumblue;">-12</span>);</span>**********</span>  

    <div><span style="font-family: Verdana, sans-serif;">********<span style="font-weight: normal;">res 的結果都為 </span>********</span>  

    <div style="display: inline !important;">

    <div style="display: inline !important;">

    <div style="display: inline !important;">

    <div style="display: inline !important;"><span style="font-family: Verdana, sans-serif;">****<span style="font-weight: normal;">**********<span style="color: mediumblue; font-weight: normal;">Banana, Kiwi</span>**********</span>****</span></div>

    </div>

    </div>

    </div>

    <span style="font-family: Verdana, sans-serif;"></span></div>

    <div style="display: inline !important;">

    <div style="display: inline !important;">

    <div style="display: inline !important;">

    <div style="display: inline !important;">****<span style="font-weight: normal;">**********<span style="color: mediumblue; font-weight: normal;"><span style="font-family: Verdana, sans-serif;">  
    </span></span>**********</span>****</div>

    </div>

    </div>

    </div>

    </div>

*   <span style="color: brown; font-family: Verdana, sans-serif;"><span style="font-size: 14px;">**substring() 和 slice() 傳正整數一樣，就不做介紹了**</span></span>

*   **<span style="font-family: Verdana, sans-serif;">substr(start,length) 的第二個參數是傳字數</span>**

    <div>**<span style="font-family: Verdana, sans-serif;"><span style="color: brown; font-weight: normal;">var</span><span style="color: black; font-weight: normal;"> str = </span><span style="color: mediumblue; font-weight: normal;">"Apple, Banana, Kiwi"</span><span style="color: black; font-weight: normal;">;</span>  
    <span style="color: brown; font-weight: normal;">var</span><span style="color: black; font-weight: normal;"> res = str.substr(</span><span style="color: mediumblue; font-weight: normal;">7</span><span style="color: black; font-weight: normal;">,</span><span style="color: mediumblue; font-weight: normal;">6</span><span style="color: black; font-weight: normal;">);</span></span>**  

    <div>****<span style="font-weight: normal;">****<span style="font-family: Verdana, sans-serif;">******<span style="color: black; font-weight: normal;">res 的結果為 </span>************<span style="font-weight: normal;"><span style="color: mediumblue;">Banana</span></span>******</span>****</span>****</div>

    </div>

    <div>****<span style="font-weight: normal;">**********<span style="font-weight: normal;"><span style="color: mediumblue; font-family: Verdana, sans-serif;">  
    </span></span>**********</span>****</div>

*   <span style="font-family: Verdana, sans-serif;"><span style="font-size: 14px;"><span style="background-color: white;">**replace() 取代特定字串  
    <span style="color: black; font-weight: normal;">str = </span><span style="color: mediumblue; font-weight: normal;">"Please visit Microsoft!"</span><span style="color: black; font-weight: normal;">;</span>  
    <span style="color: brown; font-weight: normal;">var</span><span style="color: black; font-weight: normal;"> n = str.replace(</span><span style="color: mediumblue; font-weight: normal;">"Microsoft"</span><span style="color: black; font-weight: normal;">,</span><span style="color: mediumblue; font-weight: normal;">"sincode"</span><span style="color: black; font-weight: normal;">);  
    n 的值會變為 </span>**</span></span>**<span style="color: mediumblue; font-weight: normal;">Please visit sincode!</span>**</span>

*   <span style="font-size: 14px;"><span style="background-color: white;">**<span style="font-family: Verdana, sans-serif;">charAt(index) 回傳index的字元</span>**</span></span>

    <div><span style="font-size: 14px;">**<span style="font-family: Verdana, sans-serif;"><span style="color: brown; font-weight: normal;">var</span><span style="color: black; font-weight: normal;"> str = </span><span style="color: mediumblue; font-weight: normal;">"HELLO WORLD"</span><span style="color: black; font-weight: normal;">;</span>  
    <span style="color: black; font-weight: normal;">str.charAt(</span><span style="color: mediumblue; font-weight: normal;">0</span><span style="color: black; font-weight: normal;">);            </span><span style="color: green; font-weight: normal;">// returns H</span></span>**</span></div>

    <div>**<span style="color: green; font-weight: normal;"><span style="font-family: Verdana, sans-serif;">  
    </span></span>**</div>

*   <span style="font-size: 14px;"><span style="background-color: white;">****<span style="font-family: Verdana, sans-serif;">charCodeAt(index) 回傳該字元的unicode  
    <span style="color: brown; font-weight: normal;">var</span><span style="color: black; font-weight: normal;"> str = </span><span style="color: mediumblue; font-weight: normal;">"HELLO WORLD"</span><span style="color: black; font-weight: normal;">;</span>  
    <span style="color: black; font-weight: normal;">str.charCodeAt(</span><span style="color: mediumblue; font-weight: normal;">0</span><span style="color: black; font-weight: normal;">);         </span><span style="color: green; font-weight: normal;">// returns 72</span></span>****</span></span>

*   <span style="font-size: 14px;"><span style="background-color: white;">**<span style="font-family: Verdana, sans-serif;"><span style="color: #404040;">不要把String當成Array用，會發生非預期的錯誤，常常會看到：</span>  
    <span style="color: brown; font-weight: normal;">var</span><span style="font-weight: normal;"> str = </span><span style="color: mediumblue; font-weight: normal;">"HELLO WORLD"</span><span style="font-weight: normal;">;</span>  
    <span style="font-weight: normal;">str[</span><span style="color: mediumblue; font-weight: normal;">0</span><span style="font-weight: normal;">];                   </span><span style="color: green; font-weight: normal;">// returns H 和上面結果相同</span>  
    <span style="color: #464646;">錯誤的地方在於：</span></span>**</span></span>
    *   <span style="font-family: Verdana, sans-serif;">IE5, IE6, IE7沒有用</span>
    *   <span style="font-family: Verdana, sans-serif;">這把string當成Array，但其實不是</span>
    *   <span style="font-family: Verdana, sans-serif;">str[0] = "H" 不會跑error，但是沒有用</span>

> **<span style="font-family: Verdana, sans-serif;">建議要先將string轉成array再這樣做！</span>**

*   <span style="font-family: Verdana, sans-serif;"><span style="font-size: 14px;"><span style="background-color: white;"><span style="color: brown;">**split(char)方法**</span></span></span>**<span style="color: #404040;">將string依據char分割並存成array</span>  
    <span style="color: brown; font-weight: normal;">var</span><span style="background-color: white; font-weight: normal;"> txt = </span><span style="color: mediumblue; font-weight: normal;">"a,b,c,d,e"</span><span style="background-color: white; font-weight: normal;">;   </span><span style="color: green; font-weight: normal;">// String</span><span style="background-color: white; font-weight: normal;">txt.split(</span><span style="color: mediumblue; font-weight: normal;">","</span><span style="background-color: white; font-weight: normal;">);          </span><span style="color: green; font-weight: normal;">// Split on commas</span><span style="background-color: white; font-weight: normal;">txt.split(</span><span style="color: mediumblue; font-weight: normal;">" "</span><span style="background-color: white; font-weight: normal;">);          </span><span style="color: green; font-weight: normal;">// Split on spaces</span><span style="background-color: white; font-weight: normal;">txt.split(</span><span style="color: mediumblue; font-weight: normal;">"|"</span><span style="background-color: white; font-weight: normal;">);          </span><span style="font-weight: normal;"><span style="color: green;">// Split on pipe</span>  
    <span style="background-color: white;">txt.split(</span><span style="color: mediumblue;">""</span><span style="background-color: white;">);           </span><span style="color: red;">// 特別注意使用""會把string轉成索引 0 為 "</span></span>****<span style="font-weight: normal;"><span style="color: red;">a,b,c,d,e" 的array</span></span>**</span>

</div>