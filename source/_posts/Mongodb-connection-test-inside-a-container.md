---
title: Mongodb connection test inside a container
date: 2022-07-28 01:42:40
tags: [MongoDB, container]
---

## Background

To test the connection between a container and the mongoDB.

## Steps

1. Install mongo client

  ```bash
  # Install required package
  apt-get install gnupg

  # import the MongoDB public GPG Key
  wget -qO - https://www.mongodb.org/static/pgp/server-6.0.asc | apt-key add -

  # Create a /etc/apt/sources.list.d/mongodb-org-6.0.list file for MongoDB
  echo "deb http://repo.mongodb.org/apt/debian buster/mongodb-org/6.0 main" | tee /etc/apt/sources.list.d/mongodb-org-6.0.list

  # Reload local package database.
  apt-get update

  # Install the MongoDB packages.
  apt-get install -y mongodb-org
  ```

1. Test the connection

  ```bash
  # Login to mongo
  mongo "mongodb://username:pwd@1.2.3.4:5/dbname?authSource=admin"

  # Check the DB name
  db
  ```

## Reference

- https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-debian/#install-mongodb-community-edition
