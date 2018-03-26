---
title: Install Gitlab CI runner on windows
date: 2018-03-26 11:33:49
tags: [Gitlab,CI,runner,install]
---

## Before start

To enable Gitlab-CI, you need to install runners, it is an external service to help build your project. Make sure network between Gitlab server and runner is accessible.

## Installation steps

1. [Download gitlab-runner.exe](https://docs.gitlab.com/runner/install/) to a folder, ex:`C:\GitLab-Runner`
1. Run `gitlab-runner.exe register` in Administrator command prompt.
1. Enter URL and token from `Project > settings > CI/CD > Runners settings`, choose executor as `shell`.
1. After register succeed, run `gitlab-runner.exe run`
1. Go to `Project > settings > CI/CD > Runners settings` again, you should find your runner here
{% asset_img "gitlab_runner.jpg" %}
