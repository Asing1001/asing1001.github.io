---
title: Online IDE - AWS Cloud9 introduction 
date: 2018-02-09 23:04:00
tags: [AWS, IDE, Cloud9]
---

Recently I found that AWS `Cloud9` is so good that help me coding in my chromebook.  
Here I want to share how I use it with my nodejs project, it is free, fast and easy.

1. Go to https://aws.amazon.com/tw/cloud9/
1. Click `Create environment` and choose your preference
1. Wait seconds to see your cloud9 IDE
1. To switch keyboard setting, go to `Edit` > `Keyboard mode` > `Sublime` `Vim` `Emac`  
1. Setup nodejs developement environment via terminal
    ```bash
    # Clone repo 
    git clone repo

    # Switch node version
    nvm install --lts

    # Use new version
    nvm use stable

    # Install yarn
    sudo npm install -g yarn

    # Install package
    yarn

    # Start application
    npm start
    ```
1. To browse application webpage, go to `Preview` > `Preview Running Application`
