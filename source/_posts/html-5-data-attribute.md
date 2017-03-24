---
title: HTML5 強大的新功能 data- 屬性
date: 2017-03-25 02:11:28
tags:
---

常看到HTML裡有`data-`這個屬性, 其實這是HTML5才有的，透過讓每個元素有自己的dataset，讓本來需要用ajax獲得或是hide起來的資料，可直接使用data-把值藏好！

## 範例：

存人物的多項資訊到一個DOM元素中

```html
<ul id="people">
    <li id="person1" data-yearold="30" data-company="MK">Mark</li>
    <li id="person2" data-yearold="26" data-company="AC">Andy</li>
    <li id="person3" data-yearold="29" data-company="XU">Max</li>
</ul>
```
<!-- more -->

## 取出：

```javascript
<script type ="text/javascript">
//jquery
var $ele = $('#person1');
console.log($ele.data('yearold'));
console.log($ele.data('company'));

//javascript
var person1 = document.getElementById('person1');
console.log(person1.dataset.yearold);
console.log(person1.dataset.company);
</script >
```

## 寫入
```javascript
<script type ="text/javascript">
//For jquery
var $ele = $('#person1');
$ele.data("key", "Value");
$.data($ele,"Key2","Value2");
//注意若要在DOM上面看的到data-屬性必須使用
$ele.attr("data-key", "value");

//javascript
var person1 = document.getElementById('person1');
person1.dataset.key1 = 'val1';
person1.dataset.key2 = 'val2';
</script >
```

## CSS selector 可藉此設定樣式：

```css
<style type="text/css">
    [data-key] {
        background-color: #0f0;
        width: 100px;
        margin: 20px;
    }
</style>
```