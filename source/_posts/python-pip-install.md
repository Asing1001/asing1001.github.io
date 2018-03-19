---
title: Python - handle package dependencies with requirements.txt
date: 2018-03-18 01:02:00
tags: [Python, pip, requirements.txt, SSL]
---

To create same environment in python, you must know `requirements.txt`, it includes packages dependencies and let you install by a single command.

A requirements.txt looks like this : 
```
beautifulsoup4==4.6.0
certifi==2018.1.18
chardet==3.0.4
```

### Generate requirements.txt 

```
# Without using virtual environment
pip install pipreqs
pipreqs /path/to/project

# With virtual environment
pip freeze > requirements.txt
```

### Install packages from requirements.txt : 

```
pip install -r requirements.txt
```

### pip install bypass SSL certificate : 

```bash
pip install --trusted-host pypi.python.org <package_name>

# Combine with requirements.txt
pip install --trusted-host pypi.python.org -r requirements.txt
```

## Reference
https://github.com/bndr/pipreqs
`pip install --help` is your friend.
