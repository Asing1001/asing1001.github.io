---
title: Show "Search" button on mobile keyboard
date: 2019-09-18 12:52:53
tags: [Android, IOS, Search, Keyboard, 顯示搜尋按鈕]
---

<img style="width:200px" src="/2019/09/18/Show-Search-on-mobile-devices-keyboard/search_button.jpeg">

## For Android

Only `type="search"` is required on `<input>`

## For IOS

It is required to wrap `<input type="search">` inside a `<form action>`, note that the attribute `action` is must-have.

## For all mobile devices

To sum up, the minimum requirement on mobile is:

```html
<form action>
  <input
    type="search"
  >
</form>
```

To try on mobile device, here is a live example on JSFiddle :
<script async src="//jsfiddle.net/asing1001/70vhab4e/20/embed/result,html/dark/"></script>
