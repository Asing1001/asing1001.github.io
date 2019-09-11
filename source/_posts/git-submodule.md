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

## Update submodule to latest commit

Step1 - Checkout the target version of the submodule

```bash
# Go to the submodule folder
cd projB/projA
# Checkout the target commit
git pull origin master
```

Step2 - Commit the update

```bash
# Back to the parent folder
cd ..
git add projB/projA
git commit -m "submodule projA updated"
```

## Reference

- https://stackoverflow.com/questions/8191299/update-a-submodule-to-the-latest-commit
