---
title: "Cloudcannon"
description: "Cloudcannon Matrix Docs."
lead: "CloudCannon is Jam Stack cloud content management system and hosting provider for Static Site Generators such as Jekyll, Hugo and Static, with support for more SSGs coming soon..
"
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

## Intro

A developer uploads a Jekyll site in the browser or syncs with GitHub, Bitbucket or Dropbox. 

CloudCannon builds the site, hosts it and provides an interface for non-technical people to update content.

Cloudcannon costs between $0 to $75 Per month, the average cost would be $25 Per Month.

## Setup

Go to the [CloudCannon website](https://cloudcannon.com/) and click the Get Started Free button.

Enter your details into the sign up form.

Once we’ve signed up we’re taken to our dashboard. Click Create Site.

Enter a name for the site.

This creates the site and gives us options for uploading our files. 

You can download a site to test it [here](https://github.com/CloudCannon/creative-jekyll-theme/archive/master.zip)

There’s a number of ways of getting your files on CloudCannon. To keep things simple we’re just going to upload a folder from our local computer. 

Click on the folder icon. Note: folder upload is only supported in Chrome.

Navigate to your Jekyll site and click Upload.

Once the files upload, CloudCannon builds the site.

We can view the live site by clicking on the XXXXX.cloudvent.net URL in the sidebar.

## Editables

Next, we need to do is to define areas in our HTML which non-developers can update. These are called Editable Regions and are set by adding a class of **editable** to HTML elements.

Go to Developer > Files and Open index.html in CloudCannon and add a class of editable to the h1 and p inside 

```

<div class="header-content-inner">

```

 so it becomes the following:


 ```

 <div class="header-content-inner">
  <h1 class="editable">Your Favorite Source of Free Bootstrap Themes</h1>
  <hr>
  <p class="editable">Start Bootstrap can help you build better websites using the Bootstrap CSS framework! Just download your template and start going, no strings attached!</p>
  <a href="/about.html" class="btn btn-primary btn-xl page-scroll">Find Out More</a>
</div>

 ```

 ## Giving Client Access

  Client Sharing allows our client to update their site without having to create an account.

  Go to the Site Settings / Client Sharing section and set a password for your client.

  Our non-developer can view their live site at your-site.cloudvent.net (or you can set up a custom domain).

  To update their site they just add **/update** to the URL and enter the password we set earlier.