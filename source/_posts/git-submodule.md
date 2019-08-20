---
title: GIT submodule note
date: 2019-08-20 23:17:24
tags: [GIT, submodule]
---

## Clone repository with submodule

```bash
git clone --recursive <repo_url>
```

## Clone submodules after repository cloned

```bash
git submodule init
git submodule update --recursive
```

## Add submodule

```bash
git submodule add <submodule_clone_url> <submodule_folder>
```

## Remove submodule

Step1 - Remove submodule folder

```bash
git rm --cached /path/to/submodule
rm -rf /path/to/submodule
```

Step2 - Remove submodule config in `.gitmodules`

```diff
-[submodule "themes/next"]
- path = themes/next
- url = https://github.com/Asing1001/hexo-theme-next.git
[submodule "themes/next-reloaded"]
path = themes/next-reloaded
url = https://github.com/Asing1001/hexo-next.git
```
