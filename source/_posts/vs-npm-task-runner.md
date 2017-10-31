---
title: Visual Studio NPM Task Runner
date: 2017-10-30 16:22:26
tags: ["Visual Studio", "Extension", "Tool", "npm"]
---

Recently my co-worker recommends a great VS extension [NPM task runner](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.NPMTaskRunner). Instead of running NPM task via a separate terminal, it will discover NPM task via package.json and run them inside Visual Studio by a double-click.

Install via `Tools > Extensions and Updates > Online > Search NPM task runner`
{% asset_img "extension.jpg" %}

Task Runner Explorer locate in `View > Other Windows > Task Runner Explorer`
Run task by double-click tasks in sidebar, close it by `x` button
{% asset_img "task-runner.jpg" %}

If your task fails, it probably references to wrong NPM or Node.js, to fix it change the order in `Tools > Options > Projects and Solutions > External Web Tools`. I lift-up `${PATH}` to the second one.
{% asset_img "setting.jpg" %}