+++
date = '2024-11-04T14:00:14Z'
draft = false
tags = ['Mongo']
title = 'Setup Mongo Database in Linux Mint'
+++

To install Mongo db in linux mint first follow [these steps](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/).

Then create the following folder structure `mkdir /data/db`, make it writable to everyone with `sudo chmod -R go+w /data/db`.

Create a service script with `sudo vim /etc/systemd/system/mongod.service` and add the following contents:

```bash
[Unit]
Description=MongoDB Database Service
Wants=network.target
After=network.target

[Service]
ExecStart=/usr/bin/mongod --config /etc/mongod.conf
ExecReload=/bin/kill -HUP $MAINPID
Restart=always
User=mongodb
Group=mongodb
StandardOutput=syslog
StandardError=syslog

[Install]
WantedBy=multi-user.target
```



References:
* [Mongo DB /data/db directory](https://stackoverflow.com/a/42447303)
* [Mongo Can't start service](https://www.digitalocean.com/community/questions/mongo-cant-start-service)
* [Running Mongo DB on Ubuntu](https://stackoverflow.com/questions/37014186/running-mongodb-on-ubuntu-16-04-lts)
