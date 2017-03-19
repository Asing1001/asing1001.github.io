---
title: Javascript 中參數 this 的意義、呼叫function的三種方法
date: 2014-10-28 00:31:00
tags: [JavaScript]
---

**this 代表"擁有"這個 function 的 object**  
如果從全域(什麼都沒有包)直接呼叫，那麼this就是window object，如下所示：
```Javascript
function myFunction() {
    return this;
}
myFunction();
// Will return the window object
```

若改用`myobject`包起來，this就會變成 `myobject`，如下：
```Javascript
var myObject = {
    firstName: "John",
    lastName: "Doe",
    fullName: function () {  
        return this;  
    }  
}  
myObject.fullName(); 
// Will return [object Object] (the owner object)
```


了解this是什麼後，要告訴大家JavaScript中呼叫function的三種方法：

1. 直接使用function的名稱呼叫：  
```Javascript
myObject.fullName();
```
2. 使用call()呼叫，此時第一個參數是傳入你要綁定的this，可藉此設定this是誰：
```Javascript
function myFunction(a, b) {  
    return a * b;  
}  
myFunction.call(myObject, 10, 2);      
// Will return 20
```
3.  使用apply()呼叫，除了第一個參數也是傳this進去之外，差別在於第二個參數是傳array進去：
```Javascript
function myFunction(a, b) {  
    return a * b;  
}  
myArray = [10,2];  
myFunction.apply(myObject, myArray);   
// Will also return 20
```
    