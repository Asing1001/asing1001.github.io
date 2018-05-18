---
title: Find ports status on Windows
date: 2018-05-03 16:42:01
tags: [pid, port, TCP/IP, Windows, CMD, netstat, Network]
---

To find ports status on windows, there is a default Windows GUI - `Resource Monitor` or you could use `netstat` via command prompt.

## Default Windows GUI - Resource Monitor

This is the most convenient method to find port status, there are two ways to open this GUI :

1. Type `resmon` in command prompt then naviagate to `Network > Listening Ports`
2. `Ctrl+Shift+Esc to open Windows Task Manager > Performance > Resource Monitor > Network > Listening Ports`

{% asset_img "resource-monitor.jpg" %}

## Netstat

Open command prompt, type `netstat /?` to see its documentation, `netstat -abon` to list all port-proccess mapping

```bash
C:\Windows\System32>netstat -abon | findstr "8080"
  TCP    0.0.0.0:8080           0.0.0.0:0              LISTENING       4
  TCP    [::]:8080              [::]:0                 LISTENING       4

# Include heading
C:\Windows\System32>netstat -abon | findstr "Proto 8080"
  Proto  Local Address          Foreign Address        State           PID
  TCP    0.0.0.0:8080           0.0.0.0:0              LISTENING       4
  TCP    [::]:8080              [::]:0                 LISTENING       4
```

## Reference

[Stackoverflow - How can you find out which process is listening on a port on Windows?](https://stackoverflow.com/questions/48198/how-can-you-find-out-which-process-is-listening-on-a-port-on-windows?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa)