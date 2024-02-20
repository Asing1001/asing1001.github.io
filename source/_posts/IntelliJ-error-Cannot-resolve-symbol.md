---
title: Resolving IntelliJ 'Cannot Resolve Symbol' Error
date: 2023-11-21 16:21:40
tags: ["IntelliJ IDEA", "Error Resolution", "Maven"]
---

If you've encountered the `Cannot resolve symbol...` error in IntelliJ IDEA after switching branches, you're not alone. This frustrating issue can occur even when your code is error-free and compiles successfully from the command line.

## Solution

To resolve this issue, follow these steps:

0. Remove the `targets` folder, if it's a maven project, you could do `mvn clean`
1. Expand the Maven plugin in IntelliJ IDEA's sidebar.
2. Click the `Reload All Maven Projects` button with the refresh icon.

{% asset_img "intellij-error.png" %}

By following these steps, you can make the `Cannot resolve symbol...` error vanish and continue coding smoothly. This simple fix can save you time and frustration.

## Reference

For more details and community discussions on this issue, check out [this Stack Overflow thread](https://stackoverflow.com/questions/5905896/intellij-inspection-gives-cannot-resolve-symbol-but-still-compiles-code?page=1&tab=scoredesc#tab-top).
