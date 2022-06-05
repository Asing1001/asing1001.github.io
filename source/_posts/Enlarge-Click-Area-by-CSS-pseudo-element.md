---
title: Enlarge Click Area by CSS pseudo element
date: 2022-06-06 01:15:35
tags: [css, pseudo element, enlarge click area]
---

An utility class `.enlarge-click-area` to enlarge the click area of any elements.

## Plain CSS

```css
.enlarge-click-area {
  position: relative;
}
.enlarge-click-area::after {
  content: "";
  display: block;
  position: absolute;
  left: 0;
  top: 0;
  width: 160%;
  height: 160%;
  /* How to calculate 18.75%:
    Extra width for left-hand side: (160% - 100%) / 2 = 30%
    Transform percentage will relative to the width: 30% / 160% = 18.75%
  */
  transform: translate(-18.75%, -18.75%);
}
```

## SCSS

```scss
=enlargeClickArea($ratio: 2)
  position: relative

  &:after
    $offset: percentage((1 - $ratio) / 2 / $ratio)

    content: ''
    display: block
    position: absolute
    left: 0
    top: 0
    width: percentage($ratio)
    height: percentage($ratio)
    transform: translate($offset, $offset)
```
