---
title: Install Gitlab CI runner on windows
date: 2018-03-26 11:33:49
tags: [Gitlab,CI,runner,install]
---

## Before start

To enable Gitlab-CI, you need to install runners, it is an external service to help build your project. Make sure network between Gitlab server and runner is accessible.

## Install

1. [Download gitlab-runner.exe](https://docs.gitlab.com/runner/install/) to a folder, ex:`C:\GitLab-Runner`
1. Run Command prompt(Administrator):

    ```bash
    gitlab-runner.exe register
    ```

1. Enter URL and token from `Project > settings > CI/CD > Runners settings`, choose [executor](https://docs.gitlab.com/runner/executors/) as `shell`.
1. After register succeed, run

    ```bash
    gitlab-runner install
    gitlab-runner start
    ```

1. Go to `Project > settings > CI/CD > Runners settings` again, you should find your runner here
{% asset_img "gitlab_runner.jpg" %}
1. Start using the runner by creating first `.gitlab-ci.yml` in your project root folder

## Update

1. Stop service:

    ```bash
    cd C:\GitLab-Runner
    gitlab-runner stop
    ```

1. Download the [newest binary](https://docs.gitlab.com/runner/install/) and replace current `gitlab-runner.exe`.

1. Start service:

    ```bash
    gitlab-runner start
    ```

## Uninstall

Command prompt (Administrator):

```bash
cd C:\GitLab-Runner
gitlab-runner stop
gitlab-runner uninstall
cd ..
rmdir /s GitLab-Runner
```

## Reference

https://docs.gitlab.com/runner/