---
title: Jenkins migration
date: 2018-04-10 11:15:00
tags: [Jenkins, CI, Windows]
---

1. Copy existing jenkins folder, exclude `workspace`
1. Modify jenkins port in `Jenkins.xml`, default `8080`
1. Modify AD Domain and rename an account to yours in `config.xml`
1. Create / Start Jenkins service in cmd with administrator mode:

    ```bash
    sc create <jenkins-service-name> <path/to/jenkins.exe>
    sc start <jenkins-service-name>
    ```

1. View migrated jenkins in your browser with port specify above, default http://localhost:8080
