---
title: '[Drone CI] migrate pipeline config from 0.x to 1.x'
date: 2019-09-11 17:24:25
tags: [Drone, migrate, config, plugin, CI]
---

## New syntax for pipeline and step

```diff
- pipeline:
-   custom-step:
-     image: some-image
+ kind: pipeline
+ steps:
+   name: custom-step
+   image: some-image
```

## Custom plugin variables should be placed under `settings`

```diff
kind: pipeline
name: default
steps:
  name: custom-plugin
  image: some-image
- foo:
-   bar: baz
+ settings:
+   foo:
+     bar: baz
```
