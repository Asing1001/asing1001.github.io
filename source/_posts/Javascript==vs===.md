---
title: Javascript == vs === 
date: 2015-01-07 19:17:00
tags: [JavaScript]
---

今天仔細研究了Javascript中 == 和 === 的差別才知道它們會依變數型別有不同的比較方式：

## 非Object型別(String , Int...)：  
== 比 'value'  
=== 比 'value' & <span style="color: red;">'type'</span>
<!-- more -->

Example:
``` Javascript
var x = 5;  
var y = '5';  

if (x == y) {  
    console.log('same');  
} else {  
    console.log('not same');  
}  
//result：same  
```


``` Javascript
var x = 5;  
var y = '5';  

if (x === y) {  
    console.log('same');  
} else {  
    console.log('not same');  
}  
//result：not same  
```


## Object型別：
== 和 === 一樣都比較 <span style="color: red;">"Reference"</span>  

``` Javascript
var obj1 = {  
    name: "Asin",  
    weather: "Sunny"  
}  

var obj2 = {  
    name: "Asin",  
    weather: "Sunny"  
}  

var obj3 = obj2;  

var test1 = obj1 == obj2;  
var test2 = obj2 == obj3;  
var test3 = obj1 === obj2;  
var test4 = obj2 === obj3;  

console.log("test1 : " + test1);  
console.log("test2 : " + test2);  
console.log("test3 : " + test3);  
console.log("test4 : " + test4);
//Result:  
//test1 : false  
//test2 : true  
//test3 : false  
//test4 : true
```
