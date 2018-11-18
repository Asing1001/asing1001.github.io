---
title: Connect to GCP mysql through XAMPP
date: 2018-11-18 23:37:10
tags: [XAMPP, MYSQL, GCP]
---

## Requirement

Connect to a cloud mySQL DB through XAMPP

## Solution steps

1. Go to [Google Cloud Platform (GCP)](https://console.cloud.google.com)
1. Select **SQL** from the sidebar
    {% asset_img "sql.png" %}
1. Create a mysql instance, please do **keep your password**
    {% asset_img "create.png" %}
1. Wait a few minutes for Google setup the mysql instance
1. Click your instance name
1. Go to **overview** tab and find mysql IP address
    {% asset_img "mysql-ip.png" %}
1. Open XAMPP phpMyAdmin Config, located in `XAMPP > Apache > Config > phpMyAdmin(config.inc.php)`
    {% asset_img "xampp.png" %}
1. Edit following lines in the configuration
    ```php    
    /* Authentication type and info */
    $cfg['Servers'][$i]['user'] = 'root';
    $cfg['Servers'][$i]['password'] = '<your password>';
    
    /* Bind to the localhost ipv4 address and tcp */
    $cfg['Servers'][$i]['host'] = '';    
    ```    
1. Go to **Authorization(連線設定)** tab
1. Click `Add network` under public ip
1. Paste your ip address which could find by [What is my ip](http://ipv4.whatismyv6.com/)
    {% asset_img "add-network.png" %}
1. Start your Apache, go to http://localhost/phpmyadmin/ and find it is connected, enjoy :)

## Reference

- https://cloud.google.com/sql/docs/mysql/connect-admin-ip?hl=zh-tw#connect