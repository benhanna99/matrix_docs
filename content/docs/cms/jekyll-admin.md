---
title: "Jekyll Admin"
description: "Jekyll Admin Matrix Docs."
lead: "Jekyll Admin currently works only when the Jekyll server is run locally on your computer.
"
date: 2021-03-16T08:43:34+01:00
lastmod: 2021-03-16T08:43:34+01:00
draft: false
images: []
menu:
  docs:
    parent: "cms"
weight: 210
toc: true
---

## Install Jekyll Admin

Run this command in your Root Directory

```

gem install jekyll-admin

```

## Set Up Jekyll Admin as Dependency 

Add the Plugin to Jekyll Config File.

Open _config.yml and add and save:

```

gems: [jekyll-admin]


```

Next run  **jekyll serve --watch**

## Open Jekyll Admin

go to http://localhost:4000/admin