---
title: "MySQL Commands"
description: "You can use these to manage mysql when logged in over SSH"
lead: "You can use these to manage mysql when logged in over SSH"
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "cli"
weight: 130
toc: true
---

**Note Change anything that is " XXX_XXX " below to your own naming convention/ code**

EG **XXX_XXX**;

## Open MYSQL

When logged into server over SSH

```

mysql -u root -p

```

## How to Restart mySQL

```

sudo service mysql restart

```


## How to Stop mySQL

```

sudo service mysql stop;

```

## How to Start mySQL

```

sudo service mysql start;


```

## Show Databases

To list all databases run the command:

```

SHOW DATABASES;

```

## Drop Existing Database

This is optional. Drop an existing database.

```

DROP DATABASE IF EXISTS XXX_XXX;

```

## Create the new Database

```

CREATE DATABASE XXX_XXX;

```

## Create a New User

Identified by is the password
```

CREATE USER 'XXX_XXX'@'localhost' IDENTIFIED BY 'XXX_XXX';

```

## Grant all Privileges

```

GRANT ALL PRIVILEGES ON * . * TO 'XXX_XXX'@'localhost';

```

## Flush Privileges

```

FLUSH PRIVILEGES;

```

## Create a MYSQL Dump via SSH

[How to make a MYSQL Dump with Command Line](https://www.sqlshack.com/how-to-backup-and-restore-mysql-databases-using-the-mysqldump-command/)


We need to enter our relevant MYSQL database details into the brackets below. 

These can usually be found in a config.php or database.php file. For example, for a Wordpress website, the details could be found in wp-config.php

So it would look like this:


```

mysqldump -u [USERNAME] –p [DATABASE NAME] > [ARCHIVENAME.sql]


```

AND This is what we would paste in to our terminal (no brackets)#

Obviously replace the words in caps below with your correct details:

```

mysqldump -u USERNAME -p DATABASE NAME > ARCHIVENAME.sql

```

You will then be prompted to enter the password


The database dump can be downloaded via SFTP/FTP if we go back to the root folder (might need to refresh FTP Client)
