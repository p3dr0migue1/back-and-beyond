+++
date = '2025-10-23T09:05:54+01:00'
draft = true
tags = ['Mongo']
title = 'Mongo Command Not Found'
+++

If you are getting "Command Not Found" (after installing the latest mongo docker image) when running:

```bash
$ docker exec -it <mongo_container> /bin/bash
# mongo
```

This is because mongo shell has been removed from MongoDB 6.0. The replacement is [mongosh](https://www.mongodb.com/docs/mongodb-shell/).


References: [mongo: command not found on mongodb 6.0 docker container](https://stackoverflow.com/questions/73582703/mongo-command-not-found-on-mongodb-6-0-docker-container)
