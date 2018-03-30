---
title: VSCode - Fix eslint autofix not work in .vue file
date: 2017-06-13 00:32:16
tags: ["debug", "eslint", "IDE", "vscode", "autofix"]
---

1. Install `ESLint` extension
1. Open `settings.json` by pressing `Ctrl,`
1. Add following setting

    ```json
    "eslint.validate": [
        { "language": "vue", "autoFix": true }
    ]
    ```

1. (Optional) Add `"eslint.autoFixOnSave": true` for autofix on save.

1. It should work now, enjoy :)
