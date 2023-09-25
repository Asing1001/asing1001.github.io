---
title: SSH to server without password
date: 2021-09-15 03:26:00
tags: [ssh, without password, authorized_keys, PubkeyAuthentication]
---

## The requirement to ssh to server without password

To ssh without password, you must meet the condition:

- Private key in client `~/.ssh/`
- Public key in server `~/.ssh/authorized_keys`

## Steps to setup

1. Create ssh key pairs by ssh-keygen

  ```bash
  # Generate key
  ssh-keygen

  # Check the generated key pair
  ls ~/.ssh
  -rw-------  1 sing  staff  1679 Jun  8  2018 id_rsa
  -rw-r--r--  1 sing  staff   404 Jun  8  2018 id_rsa.pub
  ```

1. Login to your server
1. Copy the content of the publicKey (id_rsa.pub) to server's `~/.ssh/authorized_keys`

  ```bash
  echo "${public key content}" >> ~/.ssh/authorized_keys
  ```

1. Make sure the sshd setting `/etc/ssh/sshd_config` allow publickey authentication,

  ```bash
  PubkeyAuthentication yes
  ```

  Restart by `sudo systemctl restart ssh` if you modify the sshd setting.

1. Modify ssh config (~/.ssh/config) in your client to indicate which ssh key to use

  ```bash
  Host <server ip>
    IdentityFile ~/.ssh/id_rsa
  ```

1. Verify ssh without password

  ```bash
  ssh username@serverip
  ```
