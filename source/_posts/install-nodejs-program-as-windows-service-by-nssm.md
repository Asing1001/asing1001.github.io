---
title: Install nodejs program as windows service by nssm
date: 2018-05-29 14:39:55
tags: [nssm, windows service, nodejs]
---

## Steps to install windows service

1. Create a `start.bat` file with content `npm start`
1. [Download nssm](http://nssm.cc/download)
1. Extract it and go to `nssm/win64` folder
1. Type `nssm install service-name` from command prompt
1. Select `start.bat` as Application Path, you could also add your startup Arguments here
    {% asset_img "nssm.jpg" %}
1. Start service with `nssm start service-name`
1. You could find it already registered as windows service :)

## NSSM commands reference

You could type `nssm` anytime to see this document

```shell
M:\nssm-2.24\win64>nssm
NSSM: The non-sucking service manager
Version 2.24 64-bit, 2014-08-31
Usage: nssm <option> [<args> ...]

To show service installation GUI:

        nssm install [<servicename>]

To install a service without confirmation:

        nssm install <servicename> <app> [<args> ...]

To show service editing GUI:

        nssm edit <servicename>

To retrieve or edit service parameters directly:

        nssm get <servicename> <parameter> [<subparameter>]

        nssm set <servicename> <parameter> [<subparameter>] <value>

        nssm reset <servicename> <parameter> [<subparameter>]

To show service removal GUI:

        nssm remove [<servicename>]

To remove a service without confirmation:

        nssm remove <servicename> confirm

To manage a service:

        nssm start <servicename>

        nssm stop <servicename>

        nssm restart <servicename>

        nssm status <servicename>

        nssm rotate <servicename>
```

## Reference

http://nssm.cc