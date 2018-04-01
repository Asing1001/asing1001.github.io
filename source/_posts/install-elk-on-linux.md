---
title: Install ELK on linux
date: 2018-03-30 18:09:19
tags: [Elastic Stack, Elasticsearch, Logstash, Kibana, ELK, Install]
---

## Before Start

Make sure the server has internet access or you will have to download and upload packages manually. If the server doesn't, I recommend {% post_link grant-internet-access-by-ccproxy CCProxy %} to grant temporary internet access.

## Install JDK

```bash
wget -c --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u161-b12/2f38c3b165be4555a1fa6e98c45e0808/jdk-8u161-linux-x64.rpm
rpm -ivh jdk-8u161-linux-x64.rpm
```

## Elasticsearch

1. Download and install

    ```bash
    wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-6.2.3.rpm
    rpm -ivh elasticsearch-6.2.3.rpm
    ```

1. Start service

    ```bash
    # Auto start elasticsearch when computer start
    systemctl daemon-reload
    systemctl enable elasticsearch.service

    # start service
    systemctl start elasticsearch
    systemctl status elasticsearch
    ```

1. Verify Elastic search is running

    ```bash
    curl http://localhost:9200

    # If not working, you could try reboot
    reboot -r
    ```

    You could check log files under `/var/log/elasticsearch/`

1. Reference : https://www.elastic.co/guide/en/elasticsearch/reference/current/rpm.html

## Kibana

1. Download and install

    ```bash
    wget https://artifacts.elastic.co/downloads/kibana/kibana-6.2.3-x86_64.rpm
    rpm -ivh kibana-6.2.3-x86_64.rpm
    ```

1. Modify kibana config

    ```bash
    vi /etc/kibana/kibana.yml
    # Kibana port
    server.port: 5601
    # Bind to all ip address
    server.host: "0.0.0.0"
    ```

1. Start service

    ```bash
    systemctl daemon-reload
    systemctl enable kibana.service
    systemctl start kibana
    systemctl status kibana
    ```

1. Verify installation

    ```bash
    curl localhost:5601
    ```

    You can check log file under `/var/log/kibana/`

1. Reference : https://www.elastic.co/guide/en/kibana/current/rpm.html

## Logstash

1. Download and install

    ```bash
    wget https://artifacts.elastic.co/downloads/logstash/logstash-6.2.3.rpm
    rpm -ivh logstash-6.2.3.rpm
    ```

1. Modify `logstash.yml` to enable auto reload config

    ```bash
    vi /etc/logstash/logstash.yml
    config.reload.automatic: true
    config.reload.interval: 3s
    ```

1. Add first logstash config

    ```bash
    cd /etc/logstash/conf.d/
    cat > default.conf
    input {
      beats {
        port => 5044
      }
    }
    output {
      elasticsearch {
        hosts => ["http://localhost:9200"]
      }
    }
    ```

1. Start service

    ```bash
    systemctl daemon-reload
    systemctl enable logstash.service
    systemctl start logstash
    systemctl status logstash
    ```

1. Verify installation

    ```bash
    telnet 127.0.0.1 5044
    ```

    You could check log file under `/var/log/logstash/`

1. Reference : https://www.elastic.co/guide/en/logstash/current/installing-logstash.html
