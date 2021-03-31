---
title: "Shopify"
description: "Shopify Matrix Docs."
lead: "How to Develop for Shopify"
date: 2021-03-16T08:43:34+01:00
lastmod: 2021-03-16T08:43:34+01:00
draft: false
images: []
menu:
  docs:
    parent: "cms"
weight: 200
toc: true
---

## Benefits of Shopify

- If you move a client to shopify, you get a 20% affiliate share of whatever the client pays to shopify each month.
- No need to spin up server when hosting on shopify.
- No limitations. Anything you can do on self hosted platform you can do on shopify.

https://shopify.github.io/liquid/basics/introduction/

## Useful Links

- [Shopify Partners](https://www.shopify.com/partners)
- [Theming Framework](https://github.com/Shopify/themekit) 
- [Theming Docs](https://shopify.dev/docs/themes)
- [Liquid Cheat Sheet](https://www.shopify.com/partners/shopify-cheat-sheet)
- [Liquid Docs](https://shopify.github.io/liquid/basics/introduction/) 
- [Merchant Hand off Kit for training docs](https://www.shopify.com/partners/shopify-cheat-sheet)
- [Example Product CSV](https://github.com/christopherdodd/Skillshare/blob/master/products1.csv)
- [Shopify CSS Docs](https://shopify.github.io/slate.shopify.com/docs/0.14.0/css-examples/)
- [Code Snippets](https://github.com/freakdesign/Shopify-code-snippets)
- [More Code Snippets](https://github.com/vikrantnegi/shopify-code-snippets)
- [AJAX API](https://shopify.dev/docs/themes/ajax-api)

## Community

- [Shopify Dev Partners Slack](https://shopifypartners.slack.com/join/shared_invite/zt-fadywn35-y~7e2MJkJkQ4caIjmbKRpg#/)


## Free Courses
- [Offical Shopify Devs YT](https://www.youtube.com/c/shopifydevs)
- [Shopify Essentials for Web Developers](https://www.skillshare.com/classes/Shopify-Essentials-for-Web-Developers-From-Store-Setup-to-Custom-Themes/1070001866/projects)
- [Shopify Dev series](https://www.youtube.com/playlist?list=PLXQCP3o-w1Pvras8iuflJKO3tfkBT8c0c)

## Premium Courses

- [Shopify Theme Development: Build and Customise Your Own Online Store](https://www.skillshare.com/classes/Shopify-Theme-Development-Build-and-Customise-Your-Own-Online-Store/1756809856?via=user-profile)
- [Shopify Essentials for Web Developers](https://www.skillshare.com/classes/Shopify-Theme-Programming-Liquid-JSON-and-Javascript/60394778/projects)


## Creating a New Development Store

Login to Partner account  and click on stores - Then click add store and fill in the fields.

**Note:** password protection is enabled by default.


## Making Changes on a Test Site (or Test Theme)

To prevent issues on the live site when developing we need to duplicate the theme.

Under **Current theme** click:

```

Actions > Duplicate theme

```

The theme will be called *copy of CURRENT_THEME_NAME*. We can rename this under theme library.

Click actions preview instead of view to view the site with the dev theme. This can then be shared with the client or Project Managers to view changes. Anyone with this link can access the preview within the next 14 days. Since your store is in development, visitors will need the store password to enter. They won't be able to buy any of your products.

## Developing Locally

Usually you will need to install shopify locally so you can use various dev tools.

### Install Theme Kit

With [Theme Kit](https://shopify.dev/tools/theme-kit), you can use your own development tools to interact with the Shopify platform in the following ways:

- Use workflow tools like Git to work with a team of theme developers.
- Upload themes to multiple environments.
- Watch for local changes and upload them automatically to Shopify.
- Work on Linux, macOS, and Windows.

On windows, open terminal as admin & install Theme Kit with [Chocolatey](https://chocolatey.org/) by running the following command:

```

choco install themekit

```

### Generate API credentials

After you install Theme Kit, you need to generate new Shopify API credentials to connect Theme Kit to your store and manage your template files. Theme Kit manages its connection using a private app.

- From your Shopify admin, click Apps.
- Near the bottom of the page, click Manage private apps.
- If private app development is disabled, then click Enable private app development. Only the store owner can enable private app development.
- Click Create new private app.
- In the App details section, fill out the app name and your email address.
- In the Admin API section, click Show inactive Admin API permissions.
- Scroll to the Themes section and select Read and write from the dropdown.
- Click Save.
- Read the private app confirmation dialog, then click Create app.

Your new, unique access credentials are visible in the Admin API section. Copy the password. You’ll use it in the next step.


### Connect to an existing theme

When making changes locally and pushing live, generally you would not want to do this on the live theme, so we would use the copy of the theme we duplicated and renamed in the previous section.

To connect to an existing theme, you'll need the theme's ID. The easiest way to get your theme's ID is to use the theme get command. Make sure to replace your-password with the API password that you generated in step 2 and your-store with your store's domain name:


```

theme get --list -p=[your-password] -s=[your-store.myshopify.com]

```
EG (shorthand):

```

theme get --list -p=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 -s=matrixinternet.myshopify.com

```


if shorthand does not work ty the log form

```

theme get --list --password=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 --store=matrixinternet.myshopify.com

```


### Set up your config file

A config.yml file creates a local connection to your Shopify store’s theme. You can use the previous information you collected (API password and theme ID) to create a config.yml file in your theme, and then download the theme locally.

Create a directory for your theme:

```

mkdir [your-theme-name]

```

Navigate to the new directory:

```

cd [your-theme-name]

```

To download a specific theme, and create the config.yml file that connects this theme with a local version in the directory you just created, run the following command (without brackets).

note: you can find theme ID by going to online store > actions > edit code..........
......The themes ID will display in the URL, something like **https://matrixinternet.myshopify.com/admin/themes/119501160619**

```
theme get -p=[your-password] -s=[your-store.myshopify.com] -t=[your-theme-id]

```

eg:

```

theme get -p=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 -s=matrixinternet.myshopify.com -t=119510892715

```

### Push updates to your theme

Now that you've established a connection to a Shopify theme, you can run the following command in your theme directory:

```

theme watch

```

The theme watch command instructs Theme Kit to watch for any changes made to your local files, and automatically pushes changes to your theme in the connected Shopify store. To close the watch connection, type **ctrl + c**

At this point it is not recommended to use the code editor inside shopify dashboard as it would cause discrepancies with the code locally, otherwise we would need to run update theme.

## Tips

You should always duplicate your theme before you edit its code. This allows you to just go back and start from scratch whenever something goes wrong. After using your Shopify login credentials to access your store, go to “Online Store” > “Themes”, then select the “Duplicate” option from the “Actions” dropdown menu next to the theme you want to duplicate. 

Sections are the heart of any theme.

Templates need to be created on the live theme manually before creating the locally. Its an annoying extra step in shopify.

## Styling 

Shopify auto compiles SCSS, you don't need to set anything up.

The main theme CSS/SCSS file is usually called something like **theme.scss.liquid** and located in the **“Assets”** folder. In your theme, it may be called something slightly different. If you can’t find “theme.scss.liquid”, look for another file with “scss” or “css” in the title. 


Shopify allows us to use liquid syntax in our stylesheets. 


```

body {
  background-color: {{ settings.colors.body_background }}
}


```

Including a stylesheet looks like this in Shopify

```

<link type="text/css" href="{{ 'styles.css' | asset_url }}" rel="stylesheet">

```

For an SCSS file, it would be:


```

<link type="text/css" href="{{ 'styles.scss.css' | asset_url }}" rel="stylesheet">


```

You will find yourself working a lot in the **sections** folder when developing for Shopify. This is where you would for example, add a new section block that would be used as a slider.
It is good practice in Shopify to add your styles at the end of the section file. For example, imagine we are working in a file called slideshow.liquid in the sections folder.

Towards the bottom of the file, we would add the following liquid syntax

```

{% style %}

{% endstyle %}

```

This is basically the same as:

```

<style>
</style>


```

Here we would add our styles, EG:

```

{% style %}

 .new-slider {
    position: relative;
    width: 100%;
 }

{% endstyle %}


```
