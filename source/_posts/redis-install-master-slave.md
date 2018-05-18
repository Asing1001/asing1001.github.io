---
title: Install Redis master-slave-sentinel on linux 
date: 2018-05-18 19:30:36
tags: [redis, HA, install, linux, master, slave]
---

# Before start

1. [Download and install redis from official site](https://redis.io/download)
2. redis excutable commands are under `bin` folder, configs are under `etc` folder, logs are under `var` folder

## Redis master

### Configuration

```yaml

# Run as background service
daemonize yes

# for daemonized pid file path
pidfile "/var/run/redis_6379.pid"

# specify log file path
logfile "/var/log/6379.log"

# Set the number of databases, from 0 to 16
databases 16

# specify db dump path
dbfilename dump.rdb

# db will written into this directory
dir "/var/dump/"

# specify redis instance port
port 6379

# bind your public/local ip, to let you access by your ip address
bind ip1 ip2 ip3

# Setup your password (recommend!)
requirepass password
```

### Start Master

```bash
redis-server /redis/etc/{master.config}
```

### Verify Master

```bash
redis-cli -h 127.0.0.1 -p 6379 info replication
```

## Redis slave

### Configuration

Repeat master configuration, the only difference are two lines : 

```bash
# Specify master instance location
slaveof 192.168.1.1 6379

# For master authentication
masterauth password
```

### Start Slave

```bash
redis-server /redis/etc/{master.config}
```

### Verify Slave

```bash
redis-cli -h 127.0.0.1 -p 6379 info replication
```

## Sentinel

### Create sentinel.conf

```yaml
port 26379
sentinel monitor master 127.0.0.1 6379 1
sentinel down-after-milliseconds master 3000
sentinel failover-timeout master 18000
sentinel parallel-syncs master 1
```

### Start sentinel

```bash
redis-server.exe sentinel.conf --sentinel
```

### Verify sentinel

```bash
redis-cli -h 127.0.0.1 -p 26379 info sentinel
```

## Useful commands

```bash
ps –ef | grep redis
```

## A little note for yaml format

* Normally you don't need quote for string, 
* If string contains special character, use quote `""` or `''`
* Difference between `""` or `''` is double quote parse escape character but single quote doesn't