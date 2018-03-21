---
title: Git commands cheatsheet
date: 2018-02-08 18:29:07
tags: ["Git", "cmd"]
---

```bash
# Roll back only one folder to one commit
git checkout hashOfCommit folderName

# Discard every change
git reset --hard

# Rebase
git pull --rebase

# Check commit's message and change(-p)
git log -p -2

# Update to latest submodules
git submodule update --recursive --remote
```