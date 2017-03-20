---
title: 使用Python argparse處理command line arguments
date: 2017-03-20 22:08:51
tags: [Python]
---

## 前言

今天專案需要傳argument進python，發覺內建的argparse很好用，記錄簡易用法如下：

## Example :

```python
import argparse

parser = argparse.ArgumentParser()
parser.add_argument("-foo")
args = parser.parse_args()

print(args.foo)
```

## 測試結果

```bash
C:\pytest>argparse-test.py -foo=bar
bar

C:\pytest>argparse-test.py -foo="bar"
bar

C:\pytest>argparse-test.py -foo bar
bar

C:\pytest>argparse-test.py
None
```