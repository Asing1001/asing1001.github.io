---
title: Generate Let's Encrypt certificate manually by DNS challenge
date: 2022-05-28 18:12:05
tags: [Let's Encrypt, DNS, Certificate, https, docker]
---

## Steps

1. Use the certbot command with docker:

  ```sh
  docker run -it certbot/certbot certonly --preferred-challenges dns --manual
  ```

1. Answer the questions

  {% asset_img "questions.png" %}

1. Go to your DNS provider to add the `TXT` records specified in the challenge

1. Before hitting enter, ensure your record has published by [dig tool](https://toolbox.googleapps.com/apps/dig/#TXT/_acme-challenge.mvrater.com.)

1. Hit enter then you will get the certificates

  {% asset_img "challenges.png" %}

## Reference

- [Let's encrypt - How it works?](https://letsencrypt.org/how-it-works/)
