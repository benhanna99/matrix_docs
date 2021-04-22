---
title: "ExpressionEngine"
description: "Expression Engine Matrix Docs."
lead: "Learning ExpressionEngine"
date: 2021-03-16T08:43:34+01:00
lastmod: 2021-03-16T08:43:34+01:00
draft: false
images: []
menu:
  docs:
    parent: "cms"
weight: 220
toc: true
---

[Download ExpressionEngine](https://expressionengine.com/#ee6-download)
[Join the Slack Channel](https://expressionengine.com//blog/join-us-in-slack)
[EE Docs](https://docs.expressionengine.com/)

Note depending what version of EE you are on, the admin is very different, however teh fundamental concepts remain the same. Check what version you are on and make sure the documentation version is the same should you need to reference it. 

# Server Compatibility Wizard

If you’re not sure whether your server meets the minimum requirements, the server wizard will run some tests and give you an answer.

[Download](https://expressionengine.com/asset/file/ee_server_wizard.zip)  and unzip the archive.

    - Upload the folder to your server.
    - Point your web browser to the folder. For example: https://example.com/ee_wizard

# Download and unzip Expression Engine

[Download ExpressionEngine](https://expressionengine.com/#ee6-download) and unzip the files to a folder on your computer. Then use your favorite FTP client to upload the files to a publicly-accessible directory on your server.

# Set Permissions

Once EE is on the server it is important that the correct permissions are set. 

[Set the correct file permissions: ](https://docs.expressionengine.com/latest/installation/installation.html#3-set-file-permissions)

You can also run the following command to set permissions:

```

find system/ee \( -type d -exec chmod 755 {} \; \) -o \( -type f -exec chmod 644 {} \; \)

```

# Install ExpressionEngine using Wizard

You should have database details handy.

Open the installation wizard by adding /admin.php/ to the sites URL. eg:

http://www.ExampleSite.com/admin.php

Fill in the details, database name, database user etc and make sure the username is at least **4 characters** long.


# Install Optional Modules

Older versions of EE will bring you to "options modules" to install during the installation process. 

For Newer version, once logged in to the dashboard go to add-ons and install the ones you need:

**Typical modules needed**

- pages
- query
- file (older versions)
- search (older versions)
- email (older versions)
- jquery (older versions)


# Change Admin Area Login Name

For security reasons its common to change the name of the EE login area.

For example instead of:
http://www.ExampleSite.com/admin.php

Change to:
http://www.ExampleSite.com/unimin

To do this we rename the **system** folder. In this case we rename it to: *unimin*

Next open **admin.php** and **index.php**.

In both these files we would change the line:

```

$system_path = './system';

```

To:

```

$system_path = './unimin';

```

We can then rename **admin.php** to **unimin.php**

Obviously "unimin" is an example in this case, it could be anything you want.

[Visit the documentation: ](https://docs.expressionengine.com/latest/installation/best-practices.html) for other post install best practices you can do.


# Template Groups

On older versions of EE, Template groups are located under Design > Templates > Template Manager > New Group

Newer versions Developer > Templates.

FTP: example.com\system\user\templates

Template groups are basically template parts if you are coming from a Wordpress background, with key difference that they can be different file types, eg javascript / CSS/ HTML.

They are folders where we keep related templates. 

An example of the set up here would be:

- about
- blog
- global
- contact
- home
- layouts


Template groups are Often based on page names - Another common thing to do is match template groups with "channel" names.


# Channels

On older versions of EE: Admin > Channel Adminstration > Channels.

Newer versions: Developer > Channels.

Channels are a bucket or container for entries - we can have as many channels as we like and we can create entries for each channel.

If you are familiar with Wordpress They are basically the Custom Post Types of EE.

We would organize or different types of content in channels. EG a blog or testimonials could be in a channel.
