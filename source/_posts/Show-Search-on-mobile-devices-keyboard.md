---
title: Show "Search" button on mobile keyboard
date: 2019-09-18 12:52:53
tags: [Android, IOS, Search, Keyboard, 顯示搜尋按鈕]
---

<img style="width:200px" src="/2019/09/18/Show-Search-on-mobile-devices-keyboard/search_button.jpeg">

- In Android, only `type="search"` is required on `<input>`
- In IOS, it is required to wrap `<input type="search">` inside a `<form action>`, note that attribute `action` is must-have.

```html
<form action>
  <input
    type="search"
  >
</form>
```

Here is a JSFiddle to try on mobile device:
<script async src="//jsfiddle.net/asing1001/70vhab4e/20/embed/result,html/dark/"></script>
