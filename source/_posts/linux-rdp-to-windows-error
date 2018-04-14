---
title: Linux Remote Desktop Viewer to Windows error connecting to host
date: 2018-04-14 23:28:04
tags: ["Linux", "rdp", "Trouble Shooting"]
---

Today When I connect to Windows through `Remote Desktop Viewer` got `error connecting to host` prompt.
After searching the solution is to remove the server I'm having issue in `$home/.freerdp/known_hosts` and reconnecting again.

```bash
[sing@study ~]$ vi ~/.freerdp/known_hosts
# In Vim, remove the line start with server ip you are connecting to by `dd`, and `:wq` to save the file.
```

Reference: https://superuser.com/questions/834447/vinagre-remote-desktop-viewer-for-gnome-isnt-working-out-of-box
