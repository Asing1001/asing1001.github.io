---
title: Copy / Backup MongoDB
date: 2018-03-10 18:04:00
tags: [MongoDB]
---

Directly copy db from ip :
```
mongo 172.16.45.83 
use admin
db.runCommand({copydb:1,fromdb:"DB Name",todb:"DB Name",fromhost:"DB HOST IP"})
```

Export / Restore DB
```bash
# Export
mongodump --db dbname

# Restore
mongorestore --port <port number> <path to the backup>
# e.g. mongorestore --port 27017 X:\dump
```

If commands are unable to find, you need to go to mongodb `bin` folder first, windows default path : `C:\Program Files\MongoDB\Server\3.2\bin\`

Reference : 
https://docs.mongodb.com/manual/tutorial/backup-and-restore-tools/
