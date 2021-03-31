---
title: "Jekyll"
description: "How to set up and run Jekyll"
lead: "How to create a static site with Jekyll SSG"
date: 2020-11-12T13:26:54+01:00
lastmod: 2020-11-12T13:26:54+01:00
draft: false
images: []
menu: 
  docs:
    parent: "ssg"
weight: 20
toc: true
---

## Useful Resources

- [Jekyll Docs](https://jekyllrb.com/docs/)
- [Install Guide](https://jekyllrb.com/docs/installation/)
- [Cloudcannons (excellent) Jekyll Video Guides](https://learn.cloudcannon.com/)
- [Mike Danes Intro Course](https://www.youtube.com/watch?v=T1itpPvFWHI&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB)
- [Jekyll With Bootstrap](https://morioh.com/p/773cd1a797f0)
- [Getting Started with Jekyll](https://www.youtube.com/watch?v=iWowJBRMtpc)
- [Convert a Static site to Jeykll](https://learn.cloudcannon.com/jekyll/converting-a-static-site-to-jekyll/)
- [52 Jekyll Tutorials](https://learn.cloudcannon.com/jekyll-includes/)
- [Awesome Jekyll List](https://github.com/planetjekyll/awesome-jekyll)
- [Awesome Jekyll Plugins](https://github.com/planetjekyll/awesome-jekyll)
- [Jekyll Resources](https://jekyllrb.com/resources/)
- [Intro to Liquid](https://learn.cloudcannon.com/jekyll/introduction-to-liquid/)
- [Jekyll Cheatsheet](https://learn.cloudcannon.com/jekyll-cheat-sheet/)
- [More Jekyll Templates](https://learn.cloudcannon.com/jekyll-templates/)


## Install Ruby & Jekyll

[Install Guide](https://jekyllrb.com/docs/installation/)

## Install the jekyll and bundler gems

```

gem install jekyll bundler

```

## Create a folder

In this case we will call it **myblog**

```

mkdir myblog

```

## Change into your new directory

```

cd myblog

```


## Run the Jekyll Server with Live Reload

```

jekyll serve --watch

```

This does a build of the site to _site and runs a local development server at http://localhost:4000 by default. 

Any changes we make to a site (except edits to _config.yml) trigger the site to rebuild and the development server to refresh. 

This command is typically used while you’re developing a site as it automatically builds and serves your site locally after a change.#


You can stop the server with **ctrl + C**


Go to  [http://localhost:4000](http://localhost:4000) 

## Create Config file

In the root directory (not _site) create a file called **_config.yml**

Put some sample content in here:

```

title: Your awesome title
author:
  name: GitHub User
  email: your-email@domain.com
description: > # this means to ignore newlines until "show_excerpts:"
  Write an awesome description for your new site here. You can edit this
  line in _config.yml. It will appear in your document head meta (for
  Google search results) and in your feed.xml site description.


```

This file holds the configuration for your Jekyll site. This is commonly used to:

- Set global variables on the site
- Configure collections or defaults
- Specify runtime variables we want to run every time


## Edit Config

Open the **_config.yml** file in your folder root.

Here you can edit the Name, Url, Email etc of the website.

**IMPORTANT:** When ever you change **_config.yml** you need to restart your Jekyll server for the changes to take affect.

You can stop the server with **ctrl + C** and restart with **jekyll serve --watch** Command.

## Change the Port

This is optional but sometimes the default port 4000 is being used on your machine.

You can change the port being used by adding **port: 8080** to the config.yml file (choose a port not in use)


## _Site Folder

You should never touch this folder when editing, this is what Jeykll renders when your files are compiled when it runs.

It is the final output of everything done in Jeykll. It is the final version, you could move these files over to host server when your done.

After stopping the server, You can also use the command:

```

jekyll serve --watch

```


This builds the site to the **_site** folder. From here we would typically copy the contents of _site to a hosting provider.


## Create Layout Files

In Jekyll we can use layouts to eliminate this repetition and make the site easier to maintain.

If it does not already exist, in the **_layouts** directory in your site’s root folder, create a new file called **default.html** file with the following content:

The default.html file typically would have repeating code used globally on the site. Think Stylesheets, JS files, Nav menu, header and footer etc

```

<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
  </head>
  <body>
    {{ content }}
  </body>
</html>


```

## Layout inheritance

In the next example we’re building multiple landing pages and they’re all going to have a hero section:

If we put this hero section in _layouts/default.html it’s going to output it on every page which we don’t want. Instead, we can use layout inheritance to get around this problem. 

We’ll start by creating a new layout, **_layouts/page.html**. In Jekyll, we can set a layout within a layout, so in the page layout we’ll add the hero section then it will call the default layout which has rest of the page structure:


```

---
layout: default
---
<section class="hero">
  <div class="small-container">
    <h2>{{ page.title }}</h2>
  </div>
</section>
{{ content }}

```

We can use this layout on our landing pages and keep the rest of the pages using the default layout.


## Create the Index Page

In the root directory create **index.html** file

In this file place the following

```

---
layout: default
title: Home
---

<h1>hello World</h1>


```

Our site should now be displaying with the text "hello world".


## Add CSS

Create a folder called **css** file and create a CSS Stylesheet called **main.css**

Place some sample CSS in here if you wish, for example:

```
body {
  background-color: red;
}

```

Save the file.

Open the **default.html** file in the **_layout** directory.

Place the following code in between the **head** tag

```

<link href="{{site.baseurl}}/css/main.css" rel="stylesheet">


```

Add any other CSS files you wish to add.


## Set up SCSS

In the *css* folder rename your main.css stylesheet with the scss extension. EG main.css becomes main.scss.

Open this file and at the top we need to put a YAML header - which is 3 dashs, Enter Key and 3 more dashes

```

---
---

```

so it would now look something like this (extra h1 class added to show scss in action)

```
---
---

body {
  background-color: red;
    h1 {
      font-size: 48px;
    }
}

```

## Add Scripts

A common practice is to place scripts in a folder like **assets/js** which Jekyll will copy and place into **_site/assets/js**.

If you want the script available on every page, put the call in your default.html layout file (or footer include). 

Open the **default.html** file in the **_layout** directory. The call to the script would be something like:

```

<script src="{{site.baseurl}}/assets/js/main.js"></script>


```

## Front Matter

- [Front matter Docs](https://jekyllrb.com/docs/front-matter/)

All pages will have what is called *Front Matter*. Front Matter can be coded in Yaml or JSON. It will contain information about the page, it might contain a title or the date the post was created for example, or the author of the page.

Some examples of Front Matter are:

- Variables
- Arrays
- Objects

We will see some examples of these later.

Front Matter should be included on all the posts and pages of your site. Then you can us it to display them differently on the site.

You can create your own Front Matter Variables. This can then be accessed in the Jeykll layout. 

```

---
layout: post
title: Blogging Like a Hacker
date: 2021-03-21 15:56:67 -0700
author: "bernard"
categories: sport dev news
---

```

## Set Up Pages

Next Create some pages - EG about.html, blog.html, contact.html

Pages are the most basic building block for content. They’re useful for standalone content (content which is not date based or is not a group of content such as staff members or recipes).

The simplest way of adding a page is to add an HTML file in the root directory with a suitable filename. You can also write a page in Markdown using a .md extension which converts to HTML on build. For a site with a homepage, an about page, and a contact page, here’s what the root directory and associated URLs might look like:

```

.
├── about.md    # => http://example.com/about.html
├── index.html    # => http://example.com/
└── contact.html  # => http://example.com/contact.html

```

If you have a lot of pages, you can organize them into subfolders. The same subfolders that are used to group your pages in your project’s source will then exist in the _site folder when your site builds. However, when a page has a different permalink set in the front matter, the subfolder at _site changes accordingly.

```
.
├── about.md          # => http://example.com/about.html
├── documentation     # folder containing pages
│   └── doc1.md       # => http://example.com/documentation/doc1.html
├── design            # folder containing pages
│   └── draft.md      # => http://example.com/design/draft.html

```

A page would usually consist of some from matter. The front matter would look something like:

```

---
layout: default
title: About
permalink: /about/
---

This is my page content

```


## Permalinks

[Permalink Docs](https://jekyllrb.com/docs/permalinks/)

URLs in Jeykll are very dependant on Front matter, eg categories. Chnaging front matter can modify links. We usually won't want that.

To prevent this we add a variable called **permalink**

We can then set the URL of the page or post - see the example for the about page below.

```

---
layout: default
title: About
permalink: /my-new-url/test/about/
---

```

Checkout:

[This page for more permalink examples ](https://jekyllrb.com/docs/permalinks/).

[Variables available to us when setting permalinks for posts ](https://learn.cloudcannon.com/jekyll/permalinks#blog-post-permalinks).


## Data files

[Data Files documentation](https://jekyllrb.com/docs/datafiles/)
[Cloud Cannon Example](https://learn.cloudcannon.com/jekyll/introduction-to-data-files/)

In addition to the built-in variables available from Jekyll, you can specify your own custom data that can be accessed via the Liquid templating system.

Data files give you access information from CSV, JSON or YAML files on your Jekyll site. 

You can almost treat these files like a database.

Data files are located in the folder  **_data**. If you intend to use a data file, and this folder has not been created you will need to create it first.

[Check out this video for some examples](https://www.youtube.com/watch?v=1ckg2ttXX0s)

Data files are often used (but of course not exclusively used) for Navigation. 

We will look at this as a Data file example next

## Create Navigation Data File

Create a yml data file for the navigation items at **_data/navigation.yml.**

Inside *_data/navigation.yml* create an array of navigation items where each item has a link and a name:


```

- link: /
  name: Home
- link: /about/
  name: About
- link: /blog
  name: Blog
- link: /contact/
  name: Contact


```

We will **include** this in the header next.

## Includes

Jekyll includes let you include page fragments on your site, so we don't need to make changes to code in multiple places

Create a new folder called **_includes**

Create a new file inside the _includes directory called **navigation.html**

Create **_includes/navigation.html**. This file iterates over the navigation data file and outputs the links and adds a class="active" if it’s the current page:

```

<nav>
  {% for item in site.data.navigation %}
    <a href="{{ item.link }}" {% if item.link == page.url %}class="active"{% endif %}>
      {{ item.name }}
    </a>
  {% endfor %}
</nav>


```

Now you can use the navigation in your default layout (or anywhere you wish) by doing an include:

```

{% include navigation.html %}

```

## Posts Folder

All your posts should go into the posts folder

Blogging is baked into Jekyll. You write blog posts as text files and Jekyll provides everything you need to turn it into a blog.

Create a folder called  **_posts**.

To create a post, add a **.md** file to your **_posts** folder.

The format should be have the YEAR is a four-digit number, MONTH and DAY are both two-digit numbers, and MARKUP is the file extension representing the format used in the file. 

**2011-12-31**

For example, the following are examples of valid post filenames:

- 2021-12-31-new-years-eve-is-awesome.md
- 2020-09-12-how-to-write-a-blog.md

You should always use this naming convention.

All blog post files must begin with front matter which is typically used to set a layout or other meta data. For a simple example this can just be empty:

```

---
layout: default
title:  "Welcome to Jekyll!"
---

# Welcome

**Hello world**, this is my first Jekyll blog post.

```

## Working With Drafts

Create a folder to store the drafts by creating a folder called **_drafts** in the route directory (along with _posts)

Create  a new file eg **my-new-draft.md**

You don't have to use the date naming convention of posts - but when you are ready to publish it, move it to _posts folder and rename to the standard naming convention outlined above.

The content inside would look something like:

```

---
layout: default
---

Some draft content


```

Save it. Now stop the server and restart it with the special command:

```

jekyll serve --draft

```

If you refresh the page Drafts will show in the post list.

## List all posts

Create **blog.html** in the root of the site and add front matter to set the layout and title:

```

---
layout: page
title: Blog Page
---


```

Next we’ll output the blog posts in an unordered list, each post will have a link and title. Jekyll gives us access to an array of all the posts at site.posts. A post object has special properties. url is the URL for the generated post page, date is (by default) the date specified in the file name and title is (by default) the title specified in the file name.

Place the following code in the _layouts/page.html

```

<ul>
  {% for post in site.posts %}
    <li><a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

```


## Create Single Post Page 

Create a layout at **_layouts/posts.html**, inherit the page layout then output the title, date and content. Jekyll automatically converts the markdown content into HTML:

```

---
layout: page
---


<p>{{ page.date | date: '%B %d, %Y' }}</p>

{{ content }}

```

Now we need to add the layout in one of our posts (eg: *_posts/2011-12-31-new-years-eve-is-awesome.md*):

```

---
layout: posts
---

```


## Collections

Collections are a powerful way to organize content on your site.
They eliminate repetition and make the content easier to maintain.

- [Collections documentation](https://jekyllrb.com/docs/collections/)
- [Explain like I’m five: Jekyll collections](https://ben.balter.com/2015/02/20/jekyll-collections/)

A way of looking at them are like Custom Post Types in Wordpress, or even Categories.

**When would we usually use a collection?**

Basically If things can't logically grouped we would maybe use a page.
If things are grouped but not by date we would maybe use a collection.
If things are grouped by date then we would maybe use a post.

## Basic implementation of Collections

Defining collections happens in **_config.yml**. First we add a collections object, then under collections we define the collections we want on the site. In this case we’re going to have one collections called cookies:

```

collections:
  cookies:

  ```

Documents (the items in a collection) live in a folder in the root of the site named **_collection_name**. Documents can either be Markdown or HTML. Markdown is more common as it’s easier to work with. In this example it’s *_cookies*

Now we’ll create a document for each cookie. The image and title are specified in front matter and the description in the content. For the Afghan cookie we’ll create _cookies/afghan.md and copy the content across:

```

---
title: Afghan
image_path: https://upload.wikimedia.org/wikipedia/commons/d/d1/AfghanBiscuit.jpg
---
An Afghan biscuit is a traditional New Zealand biscuit made from flour, butter, cornflakes, sugar and cocoa powder, topped with chocolate icing and a half walnut.

```

Repeat this for the other cookies.

Next we’ll create a file **cookies.html** in the root directory with data from our cookie collection. 

Jekyll makes collection documents available to us at **site.collection_name**, in this case it’s *site.cookies*. 

In cookies.html we iterate over our documents and output the data:

```

---
layout: page
title: Cookies
---
{% for cookie in site.cookies %}
  <div class="cookie">
    <h2><img src="{{ cookie.image_path }}" alt="{{ cookie.title }}">{{ cookie.title }}</a></h2>
    {{ cookie.content }}
  </div>
{% endfor %}

```

Remember when you change **_config.yml** you need to restart your Jekyll server for the changes to take affect.

The output of this page is exactly the same and notice how much we’ve reduced the source code.

## Output collection documents as pages

We can add an **output: true** flag to our collection configuration in _config.yml which means Jekyll will generate a page for each document.

```

collections:
  cookies:
    output: true

```

Restart Jekyll.

In cookies.html we’ll remove the content and image. We’ll link the h2 tag to the generated document page. The url is available to us at document.url:

```

---
layout: page
title: Cookies
---
{% for cookie in site.cookies %}
  <div class="cookie">
    <h2><a href="{{ cookie.url }}">{{ cookie.title }}</a></h2>
  </div>
{% endfor %}

```

Now we need to create a layout for the documents. We’ll create **_layouts/cookie.html** with a basic layout:

```

---
layout: page
---
<div class="cookie">
  <h2><img src="{{ page.image_path }}" alt="page.title" />{{ page.title }}</h2>

  <div class="blog-post spacing">
    {{ content }}
  </div>
</div>


```

Then each document we can set the cookie layout:

```

---
layout: cookie
title: Afghan
image_path: https://upload.wikimedia.org/wikipedia/commons/d/d1/AfghanBiscuit.jpg
---
An Afghan biscuit is a traditional New Zealand biscuit made from flour, butter, cornflakes, sugar and cocoa powder, topped with chocolate icing and a half walnut.

```

The cookies page should now have a list of links to cookies, clicking on one should take you to a new page with information about that cookie.


## Install Jekyll Admin Plugin

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


## Host Jekyll Site on Github Pages

You should have a Git Account and Git Installed on machine.

Create a new Repository but **DO NOT** initialize it with a readme.

next open **_config.yml**

Enter the url of the Repository you just created as the baseurl, eg:

```

baseurl: "jekyll_blog_test"

```

If you had a custom domain name you would put that as the baseurl instead.

Next we upload our project to github using the following commands in this order (note you change any URLS to something relevant to your project)

```

git init

git checkout -b gh-pages

git status

git add .

git commit -m "initial commit"

git remote add origin https://github.com/benhanna99/jeykll_blog_test.git

git push origin gh-pages

```

Open the repository in Browser - check the files are all there and the branch is **gh-pages**

Then click settings.

Scroll down.

Under the title **GitHub Pages** you will see a link

Something like: 

"Your site is published at https://benhanna99.github.io/jeykll_blog_test/"

Click on the link and you should see the site is now hosted on github.



## Push Changes

Any time to make changes you can push them to the hosted site:

```

git add .

git commit -m "Commit New Change Message Here"

git push origin gh-pages

```