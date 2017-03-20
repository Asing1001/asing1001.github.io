---
title: Javascript function 的參數傳遞
date: 2014-11-05 16:30:00
tags: [JavaScript]
---

## 前言
寫過C#或JAVA的朋友一開始接觸 Javascript 是否和我一樣，覺得 Javascript funtion 參數傳遞很奇怪呢？小弟研讀一番，根據自己的理解整理了兩個迷惑的地方：

## (一) 參數多傳或少傳的結果

假設有一個 `function myfunc(x,y,z){ ……. }`當使用`myfunc(1,2)`呼叫時，傳的參數不夠多，此時不會出現exception且第三個參數會自動視為`undefined`，有點像function有「多載」的感覺！但畢竟這不是多載，最好還是給會出現undefined的參數一個初始值，如下：
```Javascript
function myfunc(x,y,z){
    if (z === undefined) {
        z = 0;
    }
}
//順帶一提，內容改為 z = z || 0; 也有一樣的效果：
function myfunc(x,y,z){   
     z = z || 0;  
}  
```
看到這裡，或許會和我一樣有個疑惑，傳四個參數會怎麼樣呢？
例如：`myfunc(1,2,3,4)`

結果是一樣不會出exception，只是第四個參數會自動忽略掉！
個人認為這是好處也是壞處，寫的時候不太會有exception，但有Bug也找不太出來……

## (二) 內建的 Arguments Object
請思考以下程式能執行嗎？
```Javascript
x = findMax(1, 123, 500, 115, 44, 88);
function findMax() {
    var i, max = 0;
    for (i = 0; i < arguments.length; i++) {
        if (arguments[i] > max) {
            max = arguments[i];
        }
    }
    return max;
}
```
可以的, 但對我這個初學者來說，認為：
1. arguments未宣告
2. 依照上述(一)的說法，參數傳太多會全部忽略！
3. 執行後結果=0

但實際執行結果是 500 !
很驚訝嗎？這是常見的Javascript語法喔！

Javascript中`function`是一個物件，`arguments`則是`function`的內建屬性，有點像一個叫做`function`的class裡面有一個array的感覺！當傳參數給`function`後，會被自動一個個存入內建的`arguments`陣列裡，因此可直接使用`arguments`來調用參數，而不需在`function`宣告一整串參數。

現在再看一次這個function，是不是豁然開朗了呢？
```Javascript
function findMax() {  
    var i, max = 0;  
    for (i = 0; i < arguments.length; i++) {  
        if (arguments[i] > max) {  
            max = arguments[i];  
        }  
    }  
    return max;  
}
```
