---
title: 使用Python argparse處理command line arguments
date: 2017-03-20 22:08:51
tags: [Python,CMD]
---

# 使用方式

今天專案需要傳argument進python，發覺內建的argparse很好用，記錄用法如下：

## 增加參數
```python
import argparse

parser = argparse.ArgumentParser()
parser.add_argument("-foo")
args = parser.parse_args()

print(args.foo)
```

### 測試結果

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

## 增加help
```python
import argparse

parser = argparse.ArgumentParser()
parser.add_argument("-foo", help="info for foo")
args = parser.parse_args()

print(args.foo)
```
### 測試結果
```bash
C:\pytest>argparse-test.py -h
usage: argparse-test.py [-h] [-foo FOO]

optional arguments:
  -h, --help  show this help message and exit
  -foo FOO    info for foo
```

## 增加 default value
```python
import argparse

parser = argparse.ArgumentParser()
parser.add_argument("-foo", help="info for foo", default="default value")
args = parser.parse_args()

print(args.foo)
```

### 測試結果
```bash
C:\pytest>argparse-test.py
default value
```

## 給予型別
```python
import argparse

parser = argparse.ArgumentParser()
parser.add_argument("-foo", help="info for foo", default=2, type=int)
args = parser.parse_args()

print(args.foo)
```

### 測試結果
```bash
C:\pytest>argparse-test.py
2

C:\pytest>argparse-test.py -foo="123"
123

C:\pytest>argparse-test.py -foo abc
usage: argparse-test.py [-h] [-foo FOO]
argparse-test.py: error: argument -foo: invalid int value: 'abc'
```

更多資訊可以參考：https://docs.python.org/3/library/argparse.html
