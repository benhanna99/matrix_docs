---
title: "Disable Binary Log"
description: "Disabling Binary Logging (only binary logging) on MySQL8"
lead: "As some of you are aware we have had a few issues with MySQL Binary Logging filling up HDD's in the last few weeks on some servers. These steps specifically refer to binary logs not general query logs, slow query logs etc. There are a couple of ways of tackling this:"
date: 2020-10-06T08:49:31+00:00
lastmod: 2020-10-06T08:49:31+00:00
draft: false
images: []
menu:
  docs:
    parent: "mysql"
weight: 10
toc: true
---

## MySQL5 & 8

In the **mysqld.cnf** in ```/etc/mysql/mysql.conf.d/mysql.cnf``` please add the following line to the bottom of the file:

```
disable_log_bin
```

This will disable the binary logging completely.

In some cases this may not work and may cause issues - if that is the case then please comment out the line (do not remove it - so other devs know it has been tried already) by adding a ```#``` in front of it and saving

If the above doesn't work we can change the time it holds the log files for by running the following commands - You can also turn it off by setting to 0

### MySQL 5
- SSH into the server
- Login to MySQL ```mysql -u root -p```
```PURGE BINARY LOGS BEFORE '2019-04-02 22:46:26';``` (Enter the appropriate date here)
```SET GLOBAL expire_logs_days = 1;```
- Logout of MySQL. (ctrl+c)
- Restart the MySQL service ```sudo service mysql restart```

### MySQL 8
- SSH into the server
- Login to MySQL ```mysql -u root -p```
- ```PURGE BINARY LOGS BEFORE '2019-04-02 22:46:26';``` (Enter the appropriate date here)
- ```SET GLOBAL binlog_expire_logs_seconds = 86400;```
- Logout of MySQL (ctrl+c)
- Restart the MySQL service ```sudo service mysql restart```