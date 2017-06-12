---
title: VSCode - Fix eslint autofix not work in .vue file
date: 2017-06-13 00:32:16
tags: ["debug", "eslint", "IDE", "vscode"]
---

1. Open `settings.json` by pressing `Ctrl,`
1. Add following setting, enjoy :)

```json
"eslint.validate": [
    { "language": "vue", "autoFix": true }
]
```
