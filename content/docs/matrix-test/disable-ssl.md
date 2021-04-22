---
title: "Disable SSL Warning"
description: "Disable SSL Warning on Matrix Test"
lead: "To prevent the Google Confidentiality Warning:"
date: 2020-03-16T08:43:34+01:00
lastmod: 2020-03-16T08:43:34+01:00
draft: false
images: []
menu:
  docs:
    parent: "matrix-test"
weight: 300
toc: true
---

# Step One

Go to Hosting & DNS" then “Hosting Settings

# Step two

Uncheck “SSL/TLS support” - it’s on by default.

Now it won’t force https anymore. 

# Step three

If you need https there’s an option for a free SSL cert from Digital Ocean. [See this guide](/docs/hosting/ssl_setup/) on setting it up.
