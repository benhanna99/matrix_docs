---
title: "Apache Commands"
description: "You can use these to manage Apache when logged in over SSH"
lead: "You can use these to manage Apache when logged in over SSH"
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "cli"
weight: 140
toc: true
---


## How to Change WP-Content Permissions

When logged into Server over SSH, navigate to the root folder of the install. Eg for the site called nfs:

```
cd /var/nfs
```

**1. Give FTP user access**

Enter the following command to change the FTP users permissions

```
chown -R 1000:www-data wp-content/ 
```

**2.  Give access back to Wordpress#**

Enter the following command to give access back to Wordpress

```
chown -R www-data:www-data wp-content/

```


## Make a Folder 777

```

sudo chmod -R 777 /var/www

```

## How to Restart Apache

```

sudo service apache2 restart

```


## Gracefully Reload Apache

```

sudo service apache2 reload

```

## Start Apache

```

sudo service apache2 start

```


## Stop Apache

```

sudo service apache2 stop

```

## Create a Backup file archive

How to create an file archive with all website files via SSH so you don't need to download each file separately (much faster)

**1. Open FTP/SFTP and find the website**

Its good to get the path here to the website we will backup.
Find the website folder and make note of the path.

**2. Connect via SSH**

Open putty.
Enter server I.P and connect.
Enter username and password.

**3. Make a Full Backup**

Navigate to the correct folder/

E.G

```

cd /var/www/

```

**4. Compress and Extract Files Using the tar Command on Linux**

[Click here for a Walktrough](https://www.howtogeek.com/248780/how-to-compress-and-extract-files-using-the-tar-command-on-linux/)

**Compress an Entire Directory or a Single File**

Use the following command to compress an entire directory or a single file on Linux.

This is much quicker than downloading via ftp/Sftp

NOTE: Make sure you change the archive name and the fold path (in this case epackaging.ie)

```

tar -czvf epackaging.ie.tar.gz epackaging.ie/

```


**5. Download Backup**

It might take a couple of minutes depending on the size of the website, but when the archive is created, there will be a new tar.gz file in the path we noted earlier. We can download this via ftp/sftp. This is much quicker than downloading the files individually.