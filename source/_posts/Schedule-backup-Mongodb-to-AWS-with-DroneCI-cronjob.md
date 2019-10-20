---
title: Schedule backup Mongodb to AWS S3 with DroneCI cronjob
date: 2019-10-18 15:42:08
tags: [Schedule backup, mongodump, DroneCI, cronjob, AWS, S3, docker, pipeline, CI]
---

To schedule backup mongodb to AWS S3 could be done extremely easy in any docker pipeline, here is an example using DroneCI docker pipeline and cronjob feature. The complete code example could be found here: https://github.com/Asing1001/mongodb-s3-backup.

1. Create `.drone.jsonnet` file using docker pipeline
2. Use `mongodump` in step1 to create archive
3. Upload the archive by `s3 plugin` in step2

  ```js
  local backupLocation = 'mongo-archive.gz';

  [{
    kind: 'pipeline',
    name: 'default',
    steps: [
      {
        name: 'mongodump',
        image: 'mongo:3.6.5',
        environment: {
          DB_URI: {
            from_secret: 'db_uri'
          },
        },
        commands: [
          'mongodump --gzip --uri="$DB_URI" --archive=' + backupLocation,
        ],
      },
      {
        name: 'upload',
        image: 'plugins/s3',
        settings: {
          bucket: 'mongo-backup',
          access_key: {
            from_secret: 'aws_access_key_id',
          },
          secret_key: {
            from_secret: 'aws_secret_access_key',
          },
          source: backupLocation,
          target: '/',
        },
      },
    ],
    trigger: {
      event: ['cron', 'push'],
      branch: 'master'
    },
  }]
  ```

4. Activate the project in DroneCI and fill up variables `aws_access_key_id`, `aws_secret_access_key`, `db_uri`
5. Setup Cron jobs in Drone project's settings
  ![drone-mongo](https://user-images.githubusercontent.com/6785698/67076974-cdc89400-f1c0-11e9-9ccc-d98ed054ec65.png)

6. Push the repository and verify the job :)

## Reference

- [Drone](https://drone.io/)
- [mongodump](https://docs.mongodb.com/manual/reference/program/mongodump/)
- [drone S3 plugin](http://plugins.drone.io/drone-plugins/drone-s3/)
