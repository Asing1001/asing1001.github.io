---
title: Git - Create empty branch
date: 2017-06-25 21:18:39
tags: [Git, branch, cmd]
---

Sometimes I want to create empty branch for gh-pages or server-packages instead of branch from master, I will excute following command:

```bash
git checkout --orphan empty.branch.name
git rm --cached -r .
echo "init empty branch" > README.md
git add README.md
git commit -m "init empty branch"
```

 [Stackoverflow reference](https://stackoverflow.com/questions/1384325/in-git-is-there-a-simple-way-of-introducing-an-unrelated-branch-to-a-repository)