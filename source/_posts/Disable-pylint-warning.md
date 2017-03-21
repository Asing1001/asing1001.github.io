---
title: Disable pylint warning
date: 2017-03-18 01:02:00
tags: [Python]
---

裝了pylint後檔案到處都被標註有問題實在有點煩，於是找了disable部分lint的方式：
<!-- more -->

1. 在project下產生.pylintrc檔案：  
`pylint --generate-rcfile > .pylintrc`

2. `.pylintrc`檔案中`[MESSAGES CONTROL]`下新增想要disable的選項，ex：  
`disable=C0111,C0103,C0303`
