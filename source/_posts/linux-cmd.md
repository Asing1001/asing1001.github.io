---
title: Linux commands cheatsheet
date: 2018-02-08 14:28:04
tags: ["Linux", "cmd"]
---

**Always use `man commandName` to know what the command is before copy and paste.**

```bash
# Show how to use a command
man command

# Find first excutable path
whichis command

# Find every excutable path
whereis command

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

# switch to last directory
cd -

# Download file with wget -c=continue download
wget -c --header "Cookie: foo=bar" http://url/to/file`

# Force reboot immediately
reboot -f

# Rename files
rename <old name> <new name> <Regex match>
```
