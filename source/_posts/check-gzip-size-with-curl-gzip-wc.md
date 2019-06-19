---
title: Measure gzip size via command line without actually compress it
date: 2018-09-03 15:10:11
tags: [gzip, curl, wc, size]
---

<!--more-->

## Measure compressed request size with curl, gzip and wc

To measure gzip sizing for a request, you don't need to actually gzip it, just use pipe `|` to pipe the stream from `curl` to `gzip` to `wc` :

```bash
# before gzip
$ curl https://www.paddingleft.com | wc -c
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 57847    0 57847    0     0  99114      0 --:--:-- --:--:-- --:--:-- 99053
   57847

# after gzip
$ curl https://www.paddingleft.com | gzip | wc -c
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 57848    0 57848    0     0   111k      0 --:--:-- --:--:-- --:--:--  110k
   10443
```

As you can see, before gzip it's 57847 bytes, after gzip it's 10443 bytes.

## Measure file size after gzip

You could do same things to measure a file gzip sizing by gzip with `-c` option, so it won't actually gzip it.

```bash
$ gzip -c foo.jpg | wc -c
    53688
```
