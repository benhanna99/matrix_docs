---
title: "Digital Ocean"
description: "Digital Ocean Hosting Setup"
lead: "How to Set Up a Digital Ocean Website"
date: 2021-03-16T08:43:34+01:00
lastmod: 2021-03-16T08:43:34+01:00
draft: false
images: []
menu:
  docs:
    parent: "hosting"
weight: 300
toc: true
---

## Creating a New Project

Enter name, description and purpose of Project

## Create a Droplet

Example

Select Ubuntu

Select shared basic plan

Select one of the European data centers and be random

Select log in with pass

Enter a password

Choose a host name - prefix it with name of project

Epackaging-ubuntu-s-1vcpu-2gb-fra1-01

## Add Domain

Under the droplet just created, click the 3 dots and select and add the domain of the website

## Connect Via SSH

Connect with I.P, Root and Password

## Install LAMP (Linux, Apache, MySQL, PHP)

.... and set it up to accept a website


The first thing we always want to when we log on, do update and upgrade, it won't effect anything, it will install tyhe latest packages we need

```

apt upgrade


```

https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-ubuntu-18-04


## Install Apache:

```

sudo apt update
sudo apt install apache2


```

We should now see the site if we paste in the server I.P into apache


## Install MYSQL:


```

sudo apt install mysql-server
sudo mysql_secure_installation


```

Validate Password component: Select No


Set up a  password
Answer Yes to all other questions

## Open MYSQL

When logged into server over SSH

```

mysql -u root -p

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

Finally Exit


## Deploy DB on Server

https://stackoverflow.com/questions/17666249/how-do-i-import-an-sql-file-using-the-command-line-in-mysql

Upload database file onto server. Now might also be a good time to upload the zip file with the websites files

CD into the folder

```

cd /var/www/html

```

## Deploy the Database:

```

mysql -u web -p epackaging < epackaging.ie.sql


```

You will be prompted to enter password

After it is uploaded, you can check the tables with the following commands:

```

-u USERNAME -p

USE DATABASE_NAME;

SHOW TABLES;


```

## Install PHP

Once again, leverage the apt system to install PHP. In addition, include some helper packages this time so that PHP code can run under the Apache server and talk to your MySQL database:

```

sudo apt install php libapache2-mod-php php-mysql

```

## Deploy Files:

http://www.rebol.com/docs/unpack-tar-gz.html

CD to path again of archive file

```

cd /var/www/html

```

To unpack a tar.gz file, you can use the tar command from the shell. 


```

tar -xzf epackaging.ie.tar.gz


```



Here's an example:


```

tar -xzf rebol.tar.gz


```

The Folder should now be unpacked on the server. Refresh the FTP client if you do not see it.

You can delete the Tar file now.

## Apache Virtual Hosts 

Next make sure vHosts are set up.

Check which sites are enabled:

```

apache2ctl -S


```

Port 80 is http

You can also check sites enabled by navigating to the FTP folder:

```

/etc/apache2/sites-available

```

Next we need to edit the ServerName, ServerAlias and DocumentRoot

Open the conf file and under **#ServerName www.example.com**. enter something similar to this 

```

ServerName www.epackaging.ie
ServerAlias epackaging.ie
ServerAdmin it@matrixinternet.ie
DocumentRoot /var/www/html/epackaging.ie/www


```


## Allow HTaccess

https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles

To make .htaccess files work as expected, you need to edit this file:

```

/etc/apache2/sites-available/default

```

Enter the following below the information we entered in the last step, making sure the directory path is correct

```

      <Directory /var/www/html/epackaging.ie/www>
                Options -Indexes
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>


```

AllowOverride All is the line that will make HTaccess work


## HTTPS

Open the default SSL conf file. Near the top should look something like this, be careful to check the path is correct

```

<IfModule mod_ssl.c>
	<VirtualHost _default_:443>
	    ServerName www.epackaging.ie
        ServerAlias epackaging.ie
		ServerAdmin it@matrixinternet.ie

		DocumentRoot /var/www/html/epackaging.ie/www

 	         <Directory /var/www/html/epackaging.ie/www>
                    Options -Indexes
                    AllowOverride All
                    Order allow,deny
                   allow from all
                </Directory>



```

Change the Path of the keys.

Find the following lines 

```

SSLCertificateFile	/etc/ssl/certs/ssl-cert-snakeoil.pem
SSLCertificateKeyFile /etc/ssl/private/ssl-cert-snakeoil.key


```

Replace them with the correct path, eg:

```


SSLCertificateFile /var/www/html/epackaging.ie/ssl/2020/epackaging.ie.csr
SSLCertificateKeyFile /var/www/html/epackaging.ie/ssl/2020/epackaging.ie.key


```

## Enable SSL

```

a2ensite
a2ensite default-ssl.conf
systemctl reload apache2

```

systemctl reload apache2

service apache2 restart


## Change Hosts File

Change Hosts file to the new I.P

Eg:

```


```

## Test Random Pages

## Install Missing Modules

## QA Checklist

## DNS - A + SPF


## Disable SSL/HTTPS If not needed

To prevent the Google Confidentiality Warning:

Go to Hosting & DNS" then "Hosting Settings

Uncheck "SSL/TLS support" - it's on by default.

Now it won't force https anymore. If you need https there's an option for a free SSL cert from Digital Ocean.


-Install LAMP (Linux, Apache, MySQL, PHP) environment and set it up to accept a website
-Deploy website on the new server
-Configure Apache, SSL, MySQL, PHP