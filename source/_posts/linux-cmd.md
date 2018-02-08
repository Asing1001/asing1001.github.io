---
title: Linux commands cheatsheet
date: 2018-02-08 14:28:04
tags: ["Linux", "cmd"]
---

**Always use `man commandName` to know what the command is before copy and paste.**

```bash
# Show how to use a command
man commandName

# Use proxy
export http_proxy=http://server-ip:port/ 
export https_proxy=http://server-ip:port/

# Check CentOS version
rpm --query centos-release

# Read file
cat filename

# Write file (after excute, type content and ctrl+d to save)
cat > filename

# RPM install
rpm -ivh file.rpm
```