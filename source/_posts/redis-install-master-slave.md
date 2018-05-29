---
title: Install Redis master-slave-sentinel on linux 
date: 2018-05-18 19:30:36
tags: [redis, HA, install, linux, master, slave]
---

## Before start

1. [Download and install redis from official site](https://redis.io/download)
2. redis excutable commands are under `bin` folder, configs are under `etc` folder, logs are under `var` folder
<!--more-->

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
redis-cli -h 127.0.0.1 -p 6379 -a password info replication
```

You should see something like this, if you have slave you will see number of `connected_slaves` :

```shell
[root@lx-uk-ssm129 redis]# bin/redis-cli -p 6379 -a password info replication
# Replication
role:master
connected_slaves:2
slave0:ip=127.0.0.1,port=8880,state=online,offset=110104326,lag=1
slave1:ip=127.0.0.1,port=8879,state=online,offset=110104386,lag=1
master_repl_offset:110104386
repl_backlog_active:1
repl_backlog_size:1048576
repl_backlog_first_byte_offset:109055811
repl_backlog_histlen:1048576
```

## Redis slave

### Configuration

Repeat master configuration, change your port, bind ip...etc, the only difference are two lines :

```bash
# Specify master instance location
slaveof 127.0.0.1 6379

# For master authentication
masterauth password
```

### Start Slave

```bash
redis-server /redis/etc/{slave.config}
```

### Verify Slave

```bash
redis-cli -h 127.0.0.1 -p 6379 -a password info replication
```

You will see something like this :

```shell
[root@example redis]# bin/redis-cli -h 127.0.0.1 -p 8879 -a password info replication
# Replication
role:slave
master_host:127.0.0.1
master_port:6379
master_link_status:up
master_last_io_seconds_ago:1
master_sync_in_progress:0
slave_repl_offset:108498274
slave_priority:100
slave_read_only:1
connected_slaves:0
master_repl_offset:0
repl_backlog_active:0
repl_backlog_size:1048576
repl_backlog_first_byte_offset:0
repl_backlog_histlen:0
```

## Sentinel

### Create sentinel.conf

```yaml
# port to run sentinel
port 26379
dir /tmp

# Consider master objectively down only if at least number of sentinels agree
sentinel monitor master 127.0.0.1 6379 1

# How many seconds master not responding will consider it as down
sentinel down-after-milliseconds master 3000

# How many slave could sentinel reconfigure simultaneously, use low number to prevent all instance unreachable at about the same time
sentinel parallel-syncs master 1

# Sentinel failover timeout
sentinel failover-timeout master 18000

```

### Start sentinel

```bash
redis-server sentinel.conf --sentinel
```

### Verify sentinel

```bash
redis-cli -h 127.0.0.1 -p 26379 info sentinel
```

## Useful commands

```bash
# check redis instance
ps –ef | grep redis

# shutdown redis process
kill PID
```

## A little note for yaml format

* Normally you don't need quote for string, 
* If string contains special character, use quote `""` or `''`
* Difference between `""` or `''` is double quote parse escape character but single quote doesn't