---
title: Check a JPEG is progressive or baseline
date: 2018-09-04 13:00:19
tags: [JPEG, progressive, baseline, curl, hexdump, shell, grep]
---

## Determine progressive JPEG by it's content

From [wiki-JPEG](https://en.wikipedia.org/wiki/JPEG), we could see a baseline/progressive JPEG have byte marker mapping differently as following:

| Short name   | Bytes       | Payload        | Name                              |
| : ---------- | :---------- | :------------- | :-------------------------------- |
| SOF0         | 0xFF, 0xC0  | variable size  | Start Of Frame (baseline DCT)     |
| SOF2         | 0xFF, 0xC2  | variable size  | Start Of Frame (progressive DCT)  |

So to tell the image is progressive JPEG, we need to check if it contains `0xFF, 0xC0` which is `c2ff` in `Two-byte hexadecimal display`.

<!--more-->

## Check a local JPEG is progressive by hexdump

We could use `hexdump` to display image contents in `Two-byte hexadecimal display` format, then `grep` to check if it contains `c2ff` which is progressive only marker

```bash
$ hexdump -x progressive.jpg | grep c2ff
0000090    1414    1414    1414    1414    1414    1414    1414    c2ff
# find c2ff so it is progressive!

$ hexdump -x baseline.jpg | grep c2ff
# no c2ff in baseline

$ hexdump -x baseline.jpg | grep c0ff
0000090    1414    1414    1414    1414    1414    1414    1414    c0ff
# baseline has c0ff
```

## Check an image url is progressive curl, hexdump and grep

We could use `curl` to fetch an image, then `hexdump` to show it in `Two-byte hexadecimal display` format, then `grep` to check if it contains `c2ff`, in short, `curl <url> | hexdump -x | grep c2ff`

```bash
$ curl https://www.paddingleft.com/2018/09/04/check-a-JPEG-is-progressive-or-baseline/progressive.jpg | hexdump -x | grep c2ff
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 47144  100 47144    0     0   118k      0 --:--:-- --:--:-- --:--:--  118k
0000090    1414    1414    1414    1414    1414    1414    1414    c2ff
# find c2ff so it is progressive!
```

## Material

Here I got one progressive JPEG and one baseline JPEG for you to test :)

### Progressive JPEG

{% asset_img "progressive.jpg" %}

### Baseline JPEG

{% asset_img "baseline.jpg" %}