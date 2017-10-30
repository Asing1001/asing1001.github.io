---
title: Visual Studio NPM Task Runner
date: 2017-10-30 16:22:26
tags: ["Visual Studio", "Extension", "Tool", "npm"]
---

Recently my co-worker recommends a great VS extension [NPM task runner](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.NPMTaskRunner). Instead of running NPM task via a separate terminal, it will discover NPM task via package.json and run them inside Visual Studio by a double-click.

Install it via Extensions and Updates.
{% asset_img "extension.jpg" %}

Task Runner Explorer, could find it in `View > Other Windows > Task Runner Explorer`
{% asset_img "task-runner.jpg" %}

If your task fails, it probably references to wrong NPM or Node.js, to fix it change the order in `Tools > Options > Projects and Solutions > External Web Tools` . For example, I lift-up `${PATH}` to the second one.
{% asset_img "setting.jpg" %}