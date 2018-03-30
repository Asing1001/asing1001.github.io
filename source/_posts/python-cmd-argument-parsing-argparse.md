---
title: Python argparse - handle command line arguments
date: 2017-03-20 22:08:51
tags: [Python,CMD,argparse]
---

Library `argparse` in python could help user handle arguments passed through command prompt, below I record the most important functions ：
<!-- more -->


## Add argument
```python
import argparse

parser = argparse.ArgumentParser()
parser.add_argument("-foo")
args = parser.parse_args()

print(args.foo)
```

### Result

```
C:\pytest>argparse-test.py -foo=bar
bar

C:\pytest>argparse-test.py -foo="bar"
bar

C:\pytest>argparse-test.py -foo bar
bar

C:\pytest>argparse-test.py
None
```

## Add --help
```python
import argparse

parser = argparse.ArgumentParser()
parser.add_argument("-foo", help="info for foo")
args = parser.parse_args()

print(args.foo)
```
### Result
```
C:\pytest>argparse-test.py -h
usage: argparse-test.py [-h] [-foo FOO]

optional arguments:
  -h, --help  show this help message and exit
  -foo FOO    info for foo
```

## Add default value
```python
import argparse

parser = argparse.ArgumentParser()
parser.add_argument("-foo", help="info for foo", default="default value")
args = parser.parse_args()

print(args.foo)
```

### Result
```
C:\pytest>argparse-test.py
default value
```

## Specify argument type
```python
import argparse

parser = argparse.ArgumentParser()
parser.add_argument("-foo", help="info for foo", default=2, type=int)
args = parser.parse_args()

print(args.foo)
```

### Result
```
C:\pytest>argparse-test.py
2

C:\pytest>argparse-test.py -foo="123"
123

C:\pytest>argparse-test.py -foo abc
usage: argparse-test.py [-h] [-foo FOO]
argparse-test.py: error: argument -foo: invalid int value: 'abc'
```

Reference：  
https://docs.python.org/3/library/argparse.html
