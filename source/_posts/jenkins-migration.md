---
title: Jenkins migration
date: 2018-03-19 01:15:00
tags: [Jenkins, CI, Windows]
---

1. Copy existing jenkins folder, exclude `workspace`
2. Modify jenkins port in `Jenkins.xml`
3. Create / Start Jenkins service in cmd with administrator mode: 
```bash
sc create <jenkins-service-name> <path/to/jenkins.exe>
sc start <jenkins-service-name>
```

4. View migrated jenkins in your browser with port specify above
