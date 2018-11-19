---
title: Connect to GCP MySQL through XAMPP
date: 2018-11-18 23:37:10
tags: [XAMPP, MySQL, GCP, SQL, Google Cloud Platform, GUI, phpMyAdmin]
---

## Background

XAMPP is the most popular PHP development environment including a great GUI - phpMyAdmin, I would like to connect it to a cloud MySQL DB - Google Cloud Platform MySQL.

## Requirement

1. [XAMPP](https://www.apachefriends.org/) installed
1. Create a [Google Cloud Platform (GCP)](https://console.cloud.google.com) account


<!-- more -->

## Solution steps

1. Go to [Google Cloud Platform (GCP)](https://console.cloud.google.com)
1. Select **SQL** from the sidebar
    {% asset_img "sql.png" %}
1. Create a MySQL instance, please do **keep your password**
    {% asset_img "create.png" %}
1. Wait a few minutes for Google setup the MySQL instance
1. Click your instance name
1. Go to **overview** tab and copy MySQL IP address, `e.g. 1.2.3.4`
    {% asset_img "mysql-ip.png" %}
1. Open XAMPP phpMyAdmin Config, located in `XAMPP > Apache > Config > phpMyAdmin(config.inc.php)`
    {% asset_img "xampp.png" %}
1. Edit following lines in the configuration
    ```php    
    /* Paste username / password */
    $cfg['Servers'][$i]['user'] = 'root';
    $cfg['Servers'][$i]['password'] = '<your password>';
    
    /* Paste MySQL ip address */
    $cfg['Servers'][$i]['host'] = '1.2.3.4';    
    ```    
1. Go to **Authorization(連線設定)** tab
1. Click `Add network` under public ip
    {% asset_img "add-network.png" %}
1. Paste your ip address, which could be found through [What is my ip](http://ipv4.whatismyv6.com/)    
1. Start XAMPP Apache, go to http://localhost/phpmyadmin/ and find it is connected, enjoy :)
    {% asset_img "phpadmin.png" %}

## Reference

- https://cloud.google.com/sql/docs/mysql/connect-admin-ip?hl=zh-tw#connect
