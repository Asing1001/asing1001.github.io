---
title: Copy / Backup MongoDB
date: 2018-03-10 18:04:00
tags: [MongoDB]
---

### Directly copy db from ip :
```bash
mongo <ip>
use admin
db.runCommand({copydb:1, fromdb:"<DB Name>", todb:"<DB Name>", fromhost:"<DB HOST IP>"})
```

### Export / Restore DB
```bash
# Export
mongodump --db <dbname>

# Restore
mongorestore --port <port number> <path to backup folder>
# e.g. mongorestore --port 27017 X:\dump
```

### Note : 

1. Run commands in administrator mode
1. If commands not found, excute commands under mongodb `bin` folder, windows default path : `C:\Program Files\MongoDB\Server\3.2\bin\`


### Reference : 
https://docs.mongodb.com/manual/tutorial/backup-and-restore-tools/
