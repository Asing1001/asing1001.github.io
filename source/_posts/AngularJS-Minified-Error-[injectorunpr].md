---
title: AngularJS Minified Error:[$injector:unpr]
date: 2015-03-10 18:04:00
tags: [AngularJS]
---

今天在把 AngularJS 的 Code 放上 Production 環境時出現了一個問題：  
[![](http://4.bp.blogspot.com/-y1VBPBSgoJ0/VP7APyORTuI/AAAAAAAAJ3g/1ErKGiWOZes/s1600/188%E9%87%91%E5%AE%9D%E5%8D%9A%2B_%2B%E9%87%91%E8%9E%8D%E6%8A%95%E6%B3%A8%EF%BC%8C%E6%82%A8%E6%9C%80%E7%90%86%E6%83%B3%E7%9A%84%E6%8A%95%E8%B5%84%E7%90%86%E8%B4%A2%E5%9C%BA%E6%89%80%E3%80%82-000069.jpg)](http://4.bp.blogspot.com/-y1VBPBSgoJ0/VP7APyORTuI/AAAAAAAAJ3g/1ErKGiWOZes/s1600/188%E9%87%91%E5%AE%9D%E5%8D%9A%2B_%2B%E9%87%91%E8%9E%8D%E6%8A%95%E6%B3%A8%EF%BC%8C%E6%82%A8%E6%9C%80%E7%90%86%E6%83%B3%E7%9A%84%E6%8A%95%E8%B5%84%E7%90%86%E8%B4%A2%E5%9C%BA%E6%89%80%E3%80%82-000069.jpg)

點擊會連到[https://docs.angularjs.org/error/$injector/unpr](https://docs.angularjs.org/error/$injector/unpr) 文件描述$injector錯誤，直接展開看minified後的JS發現`$scope被轉成a了`, 因為minified會透過縮減變數名稱節省檔案大小！

Sample code (wrong) :

```Javascript
App.controller("MyCtrl", function ($scope) {  
    $scope.foo= "foo";  
});  

//After Minified：(可透過[線上minified網站](http://refresh-sf.com/)試試看)
App.controller("MyCtrl",function(o){o.foo="foo"});
//Cause Error: [$injector:unpr] http://errors.angularjs.org/1.2.26/$injector/unpr?.....
```

解決方法：`在inject時明確指定inject的物件`
```Javascript
App.controller("MyCtrl", ["$scope", function ($scope) {  
    $scope.foo= "foo";  
}]);

//After Minified：
App.controller("MyCtrl",["$scope",function(o){o.foo="foo"}]);
//No error
```
