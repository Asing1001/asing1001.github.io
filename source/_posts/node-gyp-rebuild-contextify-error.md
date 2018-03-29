---
title: node-gyp rebuild contextify error
date: 2018-03-29 15:56:10
tags: [node-gyp,contextify,error,nodejs,npm,Trouble Shooting]
---

## TL;DR

1. `yarn why contextify`
2. Remove/Update the result dependency from step 1. by modify `package.json`.
3. `npm install`

## Full scenario

Today I encounter an error when `npm install`, the error look like this : 

```error
error M:\Github\asing1001.github.io\node_modules\contextify: Command failed.
...
...
..\src\contextify.cc(150): error C2039: 'SetAccessCheckCallbacks': is not a member of 'v8::ObjectTemplate'
```

This is caused by the package `contextify` too old, to find out which package dependent on `contextify`, I use `yarn why contextify` in command prompt :

```bash
M:\Github\asing1001.github.io> yarn why contextify
yarn why v0.22.0
[1/4] Why do we have the module "contextify"...?
[2/4] Initialising dependency graph...
[3/4] Finding dependency...
[4/4] Calculating file sizes...
info This module exists because "hexo-migrator-blogger#to-markdown#jsdom" depends on it.
Done in 2.30s.
```

Obviously it is refenrence by dependency `hexo-migrator-blogger`, I update `package.json` to remove this package and `npm install` again, it is fixed :)

