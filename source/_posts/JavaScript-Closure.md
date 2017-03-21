---
title: JavaScript Closure (封裝)
date: 2014-10-29 23:30:00
tags: [JavaScript]
---

今天練習的是Javascript裡非常重要的概念-"Closure(封裝)"
也就是和C#、JAVA等語言一樣，變數也能有Private、Public的差別！
<!-- more -->

先介紹 global variable(全域變數)和 local variable(私有變數)的差別：
`global variable` 為直接宣告並隸屬於window物件的變數
```Javascript
var a = 4;
function myFunction() {
    return a * a;
}
```
`local variable`為宣告在function內的變數
```Javascript
function myFunction() {
    var a = 4;
    return a * a;
}
```
這樣的方程式在合作開發時，由於其他人不知道你有設哪些變數，常常會造成變數衝突問題，如下：
```Javascript
var counter = 0;

function yourfunction() {
    counter =5;
    //do something....
}

var counter = 10;

function othersfunc() {
    counter += 1;
}

add();
add();
add();
// the counter is now equal to 13
```

尤其是大型專案很多JS檔，更容易發生錯誤，所以只好把全域變數變為私有變數：
```Javascript
function add() {
    var counter = 0;
    counter += 1;
}

add();
add();
add();

// the counter should now be 3, but it does not work !
```
很明顯的，這樣一來每次call這個function時，counter又再次被設為0，所以這樣也行不通！因此就要使用inner function了：
```Javascript
function add() {
    var counter = 0;
    function plus() {counter += 1;}
    plus();    
    return counter; 
}
```
這樣一來counter就變為私有變數了，然而這樣要怎麼"呼叫"函式又變成另外一個問題，因此我們要用"closure"(封裝)來解決這個難題：
```Javascript
var add = (function () {
    var counter = 0;
    return function () {return counter += 1;}
})();

add();
add();
add();

// the counter is now 3
```

1. ()自發執行函數 `(function(){ //do something  })()`
2. 在上述函數內宣告私有變數 `var counter = 0;`
3. `return function(){} 給指定物件 add`

完工！
感想：發明的人真厲害，很聰明的做法...！