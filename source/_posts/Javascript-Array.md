---
title: Javascript 陣列觀念&相關方法
date: 2014-11-01 01:39:00
tags: [JavaScript]
---

## Array的兩種宣告方式： 
```Javascript
var cars = []; 
var cars = new Arrary();
```
w3schools提到, 這兩種方式雖然都一樣，但建議用 [] 的方式來宣告，避免某些時候混淆，何況 [] 簡單又好記！
<!-- more -->

## Arrays 和 Objects 的主要差別：
arrays 使用 數字 index
objects 使用 字串 index
舉例：
```Javascript
var cars = ["Saab", "Volvo", "BMW"];    //Array
var cars2 = {"Saab", "Volvo", "BMW"};   //Object
要讀取 BMW 時：Array : cars [0]  ，Object : cars2["BMW"]
```

## Array常用方法：
```Javascript
pop() //移除最後一個item，並return它
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.pop(); // Removes the last element ("Mango") from fruits
push(item) //把item加在最後面，return 新的Length回來
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.push("Kiwi"); //Adds a new element ("Kiwi") to fruits
shift() //移除第一個並回傳
unshift() //把item加在最前面，回傳length
sort() //可依照字母排序
reverse() //依照字母倒排

//排序數字Array的方法：
//小到大：
var points = [40, 100, 1, 5, 25, 10];
points.sort(function(a, b){return a-b});
//大到小：
var points = [40, 100, 1, 5, 25, 10];
points.sort(function(a, b){return b-a});
```
