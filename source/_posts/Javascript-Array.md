title: |
	Javascript 陣列觀念&相關方法 [Javascript Array]
date: 2014-11-01 01:39:00
tags: [JavaScript]
---

<div>

### 重要觀念：Arrays 是一種特殊的 Objects

</div>

首先介紹Array的兩種宣告方式：  
var cars = [];  
或  
var cars = new Arrary();  
<a name="more"></a>  

<div style="orphans: 2; text-align: -webkit-auto; widows: 2;">w3schools提到：這兩種方式雖然都一樣，但是建議用 [] 的方式來宣告，避免某些時候混淆，何況 [ ] 簡單又好記！</div>

### Arrays 和 Objects 的主要差別是什麼 ?

<div>

*   arrays 使用 <span style="color: #cc0000;">數字 index</span>
*   objects 使用 <span style="color: #cc0000;">字串 index</span>

</div>

<div>舉例：</div>

<div>

<div><span style="font-family: Consolas, 'courier new'; font-size: 14px; orphans: 2; text-align: -webkit-auto; widows: 2;">var cars = ["Saab", "Volvo", "BMW"];    //Array</span></div>

</div>

<div>

<div><span style="font-family: Consolas, 'courier new'; font-size: 14px; orphans: 2; text-align: -webkit-auto; widows: 2;">var cars2 = {"Saab", "Volvo", "BMW"};   //Object</span></div>

</div>

<div>要讀取 BMW 時：Array : cars [0]  ，Object : cars2["BMW"]  

### Array常用方法一覽：

<div>

*   ****pop() 移除最後一個item ， 並return它  
    <span style="color: brown; font-family: Consolas, 'courier new'; font-weight: normal;">var</span><span style="color: black; font-family: Consolas, 'courier new'; font-weight: normal;"> fruits = [</span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-weight: normal;">"Banana"</span><span style="color: black; font-family: Consolas, 'courier new'; font-weight: normal;">, </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-weight: normal;">"Orange"</span><span style="color: black; font-family: Consolas, 'courier new'; font-weight: normal;">, </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-weight: normal;">"Apple"</span><span style="color: black; font-family: Consolas, 'courier new'; font-weight: normal;">, </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-weight: normal;">"Mango"</span><span style="color: black; font-family: Consolas, 'courier new'; font-weight: normal;">];</span>  
    <span style="color: black; font-family: Consolas, 'courier new'; font-weight: normal;">fruits.pop();              </span><span style="color: green; font-family: Consolas, 'courier new'; font-weight: normal;">// Removes the last element ("Mango") from fruits</span>****

*   ******push(item) 把item加在最後面，return 新的Length回來  
    <span style="color: brown; font-family: Consolas, 'courier new'; font-weight: normal;">var</span><span style="color: black; font-family: Consolas, 'courier new'; font-weight: normal;"> fruits = [</span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-weight: normal;">"Banana"</span><span style="color: black; font-family: Consolas, 'courier new'; font-weight: normal;">, </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-weight: normal;">"Orange"</span><span style="color: black; font-family: Consolas, 'courier new'; font-weight: normal;">, </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-weight: normal;">"Apple"</span><span style="color: black; font-family: Consolas, 'courier new'; font-weight: normal;">, </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-weight: normal;">"Mango"</span><span style="color: black; font-family: Consolas, 'courier new'; font-weight: normal;">];</span>  
    <span style="color: black; font-family: Consolas, 'courier new'; font-weight: normal;">fruits.push(</span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-weight: normal;">"Kiwi"</span><span style="color: black; font-family: Consolas, 'courier new'; font-weight: normal;">);       </span><span style="color: green; font-family: Consolas, 'courier new'; font-weight: normal;">//  Adds a new element ("Kiwi") to fruits</span>******

*   ****shift() 移除第一個並回傳****

*   ******unshift() 把item加在最前面，回傳length******

*   <span style="color: #404040; font-family: verdana, helvetica, arial, sans-serif;"><span style="font-size: 14px;">**sort()可依照字母排序**</span></span>

*   <span style="color: #404040; font-family: verdana, helvetica, arial, sans-serif;"><span style="font-size: 14px;">**reverse()依照字母倒排**</span></span>

*   <span style="color: #404040; font-family: verdana, helvetica, arial, sans-serif;"><span style="font-size: 14px;">**排序數字Array的方法：  

    小到大：  
    <span style="color: brown; font-family: Consolas, 'courier new'; font-weight: normal;">var</span><span style="background-color: white; color: black; font-family: Consolas, 'courier new'; font-weight: normal;"> points = [</span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-weight: normal;">40</span><span style="background-color: white; color: black; font-family: Consolas, 'courier new'; font-weight: normal;">, </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-weight: normal;">100</span><span style="background-color: white; color: black; font-family: Consolas, 'courier new'; font-weight: normal;">, </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-weight: normal;">1</span><span style="background-color: white; color: black; font-family: Consolas, 'courier new'; font-weight: normal;">, </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-weight: normal;">5</span><span style="background-color: white; color: black; font-family: Consolas, 'courier new'; font-weight: normal;">, </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-weight: normal;">25</span><span style="background-color: white; color: black; font-family: Consolas, 'courier new'; font-weight: normal;">, </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-weight: normal;">10</span><span style="background-color: white; color: black; font-family: Consolas, 'courier new'; font-weight: normal;">];</span>  
    <span style="background-color: white; color: black; font-family: Consolas, 'courier new'; font-weight: normal;">points.sort(</span><span style="color: brown; font-family: Consolas, 'courier new'; font-weight: normal;">function</span><span style="background-color: white; color: black; font-family: Consolas, 'courier new'; font-weight: normal;">(a, b){return a-b});</span>  
    大到小：  
    <span style="color: brown; font-family: Consolas, 'courier new'; font-weight: normal;">var</span><span style="background-color: white; color: black; font-family: Consolas, 'courier new'; font-weight: normal;"> points = [</span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-weight: normal;">40</span><span style="background-color: white; color: black; font-family: Consolas, 'courier new'; font-weight: normal;">, </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-weight: normal;">100</span><span style="background-color: white; color: black; font-family: Consolas, 'courier new'; font-weight: normal;">, </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-weight: normal;">1</span><span style="background-color: white; color: black; font-family: Consolas, 'courier new'; font-weight: normal;">, </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-weight: normal;">5</span><span style="background-color: white; color: black; font-family: Consolas, 'courier new'; font-weight: normal;">, </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-weight: normal;">25</span><span style="background-color: white; color: black; font-family: Consolas, 'courier new'; font-weight: normal;">, </span><span style="color: mediumblue; font-family: Consolas, 'courier new'; font-weight: normal;">10</span><span style="background-color: white; color: black; font-family: Consolas, 'courier new'; font-weight: normal;">];</span>  
    <span style="background-color: white; color: black; font-family: Consolas, 'courier new'; font-weight: normal;">points.sort(</span><span style="color: brown; font-family: Consolas, 'courier new'; font-weight: normal;">function</span><span style="background-color: white; color: black; font-family: Consolas, 'courier new'; font-weight: normal;">(a, b){return b-a});</span>**</span></span>

</div>

</div>