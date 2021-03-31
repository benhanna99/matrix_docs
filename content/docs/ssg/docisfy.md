---
title: "Docisfy"
description: "Docisfy"
lead: ""
date: 2020-10-06T08:49:31+00:00
lastmod: 2020-10-06T08:49:31+00:00
draft: false
images: []
menu:
  docs:
    parent: "ssg"
weight: 10
toc: true
---

## Set up and run Docisfy

It is recommended to install docsify-cli globally, which helps initializing and previewing the website locally.

**npm i docsify-cli -g**

## Initialize
If you want to write the documentation in the ./docs subdirectory, you can use the init command.

**docsify init ./docs**


Run the local server with **docsify serve ./docs** 

You can preview your site in your browser on **http://localhost:3000**

## Add a sidebar Menu

In the **Index.html** file:

```

<script>
  window.$docsify = {
    loadSidebar: true
  }
</script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>

```

## Example Sidebar Menu

Goes in sidebar.md

```
- [Home](/)

- [Gatsby JS](gatsby/_environment.md)
  - [Gatsby Environment Setup](gatsby/_environment.md)
  - [Gatsby Starter Themes](gatsby/_gatsby-starters.md)
  - [Install Packages & Libraries](gatsby/_install-packages.md)
  - [Navigation](gatsby/_navigation.md)
  - [Create Components](gatsby/_components.md)
  - [Create Layouts](gatsby/_layouts.md)
  - [Create Pages](gatsby/_create-new-gatsby-pages.md)
  - [Add Plugins](gatsby/_plugins.md)
  - [Create Queries](gatsby/_queries.md)
  - [Optimise SEO](gatsby/_navigation.md)
  - [Wordpress](gatsby/_navigation.md)
  - [Add Functionality](gatsby/_navigation.md)
  - [Gatsby Cheat Sheet](gatsby/_cheat-sheet.md)


```
