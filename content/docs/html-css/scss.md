---
title: "SCSS"
description: "Up and Running with SCSS"
lead: ""
date: 2021-03-16T08:43:34+01:00
lastmod: 2021-03-16T08:43:34+01:00
draft: false
images: []
menu:
  docs:
    parent: "html_css"
weight: 300
toc: true
---

## Install with NPM

```

npm install -g sass

```


## Prepare Files & Folders

Set up a new folder called **CSS** and create a new file in here called **main.css**

Next set up a new folder called **styles** and create a new file in here called **main.scss**


## Auto Compile .SCSS

When you install Sass on the command line, you'll be able to run the sass executable to compile .scss files

Open the folder with Visual Studio code.

Click Terminal > New Terminal

Run the below command


```

sass styles/main.scss css/main.css


```

## Import Styles into main.scss

Using a file editor create a new .scss file prefixed with an underscore

EG: _general.scss

Open main.scss

Import the styles as below

```

@import "_general";

```

When we add styles to _general.scss and save, the code will compile and output as css into main.css

Its a good idea to break up scss into similar files and import as above, eg _header.scss, _footer.scss


## Watch for Changes

With the following command, Sass will watch all files in the **styles** folder for changes, and compile CSS to the **css** folder.

```

sass --watch styles/main.scss css/main.css

```

## Variables

Think of variables as a way to store information that you want to reuse throughout your stylesheet. You can store things like colors, font stacks, or any CSS value you think you'll want to reuse. Sass uses the $ symbol to make something a variable. Here's an example:

```

$primary-font: 'Helvetica', sans-serif;
$secondary-font: Montserrat', sans-serif;

$primary-color: #333;
$secondary-color: #333;

```

We could then use this to add helvetica and the color white to text like below

```

body {
  font: 100% $font-stack;
  color: $primary-color;
}

```

Which would output

```

body {
  font: 100% Helvetica, sans-serif;
  color: #333;
}

```