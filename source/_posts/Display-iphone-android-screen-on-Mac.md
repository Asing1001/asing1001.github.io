---
title: Display iphone/android screen on Mac
date: 2020-11-16 19:56:17
tags: [iphone, android, mirror, cast, mac]
---

## Display iphone screen on Mac

1. Connect your iphone through wire.
2. Open `QuickTime Player`
3. File > New Movie Recording
    {% asset_img "iphone_0.jpg" %}
4. In the recording screen, select the dropdown > camera > your iphone name
    {% asset_img "iphone_1.png" %}

## Display Android Device on Mac

1. Install [scrcpy](https://github.com/Genymobile/scrcpy) by `brew install scrcpy`
2. If you don't have `adb`, run `brew cask install android-platform-tools`
3. Connect your Android phone through wire
4. excute `scrcpy`
