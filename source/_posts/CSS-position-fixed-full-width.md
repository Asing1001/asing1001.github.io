---
title: CSS padding-right disappear when position fixed width 100%
date: 2018-07-24 17:05:33
tags: [CSS, position:fixed, padding-right, calc]
---

When creating fixed navigation bar with padding, we got :

```css
position: fixed;
width: 100%;
padding: 15px;
```

However you will find padding-right disappear, the reason is the width is `window width + padding-left + padding-right`. It is exceed the window, to fix it just use `width: calc(100% - 30px)` to reduce the width

```css
position: fixed;
width: calc(100% - 30px);
padding: 15px;
```

<p data-height="265" data-theme-id="0" data-slug-hash="rrmvdZ" data-default-tab="css,result" data-user="Asing1001" data-pen-title="Fixed nav with correct padding" class="codepen">See the Pen <a href="https://codepen.io/Asing1001/pen/rrmvdZ/">Fixed nav with correct padding</a> by AsinChen (<a href="https://codepen.io/Asing1001">@Asing1001</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>