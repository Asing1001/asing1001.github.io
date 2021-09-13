---
title: Device pixel ratio - How to select a proper size image that looks sharp and display fast on different devices
date: 2021-09-14 01:39:07
tags: [Device Pixel Ratio, CSS, Android layout, iOS layout]
---

## What is Device Pixel Ratio?

The term `device pixel ratio` plays the crucial role in different languages' styling. The definition of Device pixel ratio from MDN:

> The devicePixelRatio of Window interface returns the ratio of the resolution in physical pixels to the resolution in CSS pixels for the current display device.

My translation:

```text
Device pixel ratio = (Device physical pixel width) / (Width of a device in a program)
```

For instance an `iPhone12`:

- `Physical Width`: `1170px`
- `CSS width`: `390px`
- `Device Ratio Pixel`: `1170px / 390px = 3`

## How to select a proper width image

```js
Proper image size = devicePixelRatio * width
```

If you setup a image with style `width:150px`, the phone will use `150 * 3 = 450 physical pixel` to render, so the proper width of the image should be `450`

## Common Device Pixel Ratio

{% asset_img "device-pixel-ratio.png" %}

## Reference

- [https://www.mydevice.io/](https://www.mydevice.io/)
- [https://developer.mozilla.org/en-US/docs/Web/API/Window/devicePixelRatio](https://developer.mozilla.org/en-US/docs/Web/API/Window/devicePixelRatio)
