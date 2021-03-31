---
title: "Gatsby"
description: "Gatsby"
lead: ""
date: 2020-10-06T08:49:31+00:00
lastmod: 2020-10-06T08:49:31+00:00
draft: false
images: []
menu:
  docs:
    parent: "ssg"
weight: 40
toc: true
---


## Gatsby Environment Setup

1. Install Node JS [Node](https://nodejs.org/en/).

2. Install Git CLI [git](https://git-scm.com/download/win).

3. Install gatsby via the terminal **npm i -g gatsby-cli**

4. Create the gatsby project somewhere on system  **gatsby new hello-gatsby**

5. Open the project folder **cd hello-gatsby** 

6. and open in Visual studio with **.code**

7. Open the terminal in Visual Studio Code

8. Start the project **gatsby-develop**

9. Open [local host](https://localhost:8000/).

10. Open *gatsby-config.js*

11. Under "SiteMetaData" change the title of the project to the new one

12. I recommend turning auto save on in VSC to see live updates

## Gatsby Starter Themes

We can use starter themes in Gatsby [starters](https://www.gatsbyjs.com/starters/).

Select the starter theme you wish to use and follow the install instructions.

To install you add the github url after your new projects name when creating the project

**gatsby new my-gatsby-project https://github.com/gatsbyjs/gatsby-starter-blog**
 


## Install Packages & Libraries


If the node modules folder is missing, open the terminal and install NPM packages **npm install**

===============================================

To Install BootStrap

**npm install react-bootstrap bootstrap**

import Bootstrap CSS into index.js/Component/Layout like this: **import 'bootstrap/dist/css/bootstrap.min.css';**



## Navigation, Links & Routing

**BASIC LINKS:**

first, at the top of page **import {Link} from "gatsby";**

Set the link:
```
<Link to "/test/">Navigate to test</Link>
```

If the link is external, use the standard href

```
<a href="http://google.com" target="_blank">Google</a>
```

**PROGRAMMATICALLY NAVIGATE**

first, at the top of page **import {navigate} from "gatsby";**

As a button:
```

<button onClick={()=>navigate("/test/")}>PROGRAMMATICALLY NAVIGATE</button>

```


## Create Components

Everything in Gatsby is built using components.

### Create a Header Component

Create a folder called components in the src folder.

Create a file called Header.js inside it.

**import react**

```
import React from 'react';

```

**import Link**

```
import {Link} from 'gatsby';

```

**Usually we would have a navbar in header**

If we are using react bootstrap:

```
import { 
    Navbar,
    NavbarToggler,
    NavbarBrand,
    Nav,
    NavItem,
    NavLink,
    UncontrolledDropdown,
    DropdownToggle,
    DropdownMenu,
    NavDropdown,
    DropdownItem
  } from "react-bootstrap";

```
**Create the Navbar Menu**
```
export default (props) => (
    <Navbar bg="light" expand="lg">
    <Navbar.Brand href="#home">React-Bootstrap</Navbar.Brand>
    <Navbar.Toggle aria-controls="basic-navbar-nav" />
    <Navbar.Collapse id="basic-navbar-nav">
        <Nav className="mr-auto">
        <Nav.Link as={Link} to="/">Home</Nav.Link>
        <Nav.Link as={Link} to="/">Link</Nav.Link>
        <NavDropdown title="Dropdown" id="basic-nav-dropdown">
            <NavDropdown.Item as={Link} to="/">Action</NavDropdown.Item>
            <NavDropdown.Item as={Link} to="/">Another action</NavDropdown.Item>
            <NavDropdown.Item as={Link} to="/">Something</NavDropdown.Item>
            <NavDropdown.Divider />
            <NavDropdown.Item as={Link} to="/">Separated link</NavDropdown.Item>
        </NavDropdown>
        </Nav>
    </Navbar.Collapse>
    </Navbar>
);

```

**To Render the header on a page or layout:**

```
import Header from '../components/header';
```

```
<Header />

```

**Make sure Bootstrap CSS is already imported**

```
import 'bootstrap/dist/css/bootstrap.min.css';
```

** Remember to change the link in to="/MYLINK/"**

### Create a Footer Component

Create a file called Footer.js inside components.

**import react**

```
import React from 'react';

```

**Create the functional component caller footer**

Something like this, obviously the HTML will likely be different

```

const Footer = () => (
    <footer>
        <div>
            <span className="text-muted">
                This is our Footer
            </span>
        </div>
    </footer>
);

export default Footer;

```

**import the footer into the page or layout**

```

import Footer from '../components/footer';

```

**Display the footer**

```

<Footer />

```

**For Example, in index.js**

```

export default () => (
  <div>
      <Header />
      <Footer />
  </div>
);

```

### Blog Index Component

Used on blog index page. Create a new Component called Blog.js in **components folder**

```

import React from "react"
import {Card, Button} from 'react-bootstrap';

const Blog = () => (
<Card>
  <Card.Img variant="top" src="" />
  <Card.Body>
    <Card.Title>Card Title</Card.Title>
    <Card.Text>
      Some quick example text to build on the card title and make up the bulk of
      the card's content.
    </Card.Text>
    <Button variant="primary">Go somewhere</Button>
  </Card.Body>
</Card>
);

export default Blog;

```



## Create Layouts

### Create Page Layouts

Create a folder called layouts in the **src** folder.

Create a file called Xxxxx.js inside it. I will use PrimaryLayout.js here

**import react**

```
import React from 'react';

```

**create a functional component that can receive props with a constant**

```

const PrimaryLayout = (props) => ();

```

**create the template of common elements (like header and footer) and export it.**

```

const PrimaryLayout = (props) => (
    <div>
        <Header />
            {props.children}
        <Footer />
    </div>
);

export default PrimaryLayout;

```

**remember to import the components used in the layout, in this case header and footer**

```
import Header from "../components/header";
import Footer from "../components/footer";

```

**render the layout on a page like this**

```

import React from "react"
import PrimaryLayout from "../layouts/PrimaryLayout";

export default () => (
  <div>
     <PrimaryLayout>
     
     </PrimaryLayout>
  </div>
);

```


## Create Pages

Pages are of course js files, eg **test.js**

Pages are stored in the **pages** folder in the **src** folder. Create new pages in this folder.
 
Whenever a new page is created import react at the top of the file: **import React from "react";**

Or type **imr** (using the simple react snippets extension)

Add the below code to the page to test it

```
const Test = () => (
    <div>
        <h1>This is a test Page</h1>
        <p>Inside a div as we have 2 elements</p>
    </div>
)

export default Test;
```

If there is more than one HTML element (or line)  we must put it inside a <div>

instead of a div we could use the shorthand

```
const Test = () => (
    <>
        <h1>This is a test Page</h1>
        <p>Inside a div as we have 2 elements</p>
    </>
)

export default Test;
```


**What We did**

We created a Constant (test) which is equal to a function which returns HTML. We are then exporting the component.


### Index.js

In the index.js file in the **pages** folder, insert the code from the previous tutorial. The site should now start to show.

```
import React from "react"
import PrimaryLayout from "../layouts/PrimaryLayout";

export default () => (
  <div>
     <PrimaryLayout>
     
     </PrimaryLayout>
  </div>
);

```

### blog.js

Used to display a blog index. Create a new page in **src/pages** called **blog.js**

import the blog component, primary layout and anything else needed for this page.

```

import React from "react"
import PrimaryLayout from "../layouts/primaryLayout";
import Blog from "../components/Blog";
import {Helmet} from 'react-helmet';

export default () => (
  <div>
     <PrimaryLayout>
     <Helmet>
        <meta charSet="utf-8" />
        <title>My Title</title>
        <meta name="description" content="Enter meta description" />
        <meta name="keywords" content="keywords, separated by comma" />
        <meta name="robots" content="index, follow" />
        <link rel="canonical" href="http://mysite.com/example" />
      </Helmet>
        <Blog />
     </PrimaryLayout>
  </div>
);

```

### Inner Page

Create a new page in **src/pages**

```

import React from "react"
import PrimaryLayout from "../layouts/primaryLayout";
import {Helmet} from 'react-helmet';

export default () => (
  <div>
     <PrimaryLayout>
     <Helmet>
        <meta charSet="utf-8" />
        <title>My Title</title>
        <meta name="description" content="Enter meta description" />
        <meta name="keywords" content="keywords, separated by comma" />
        <meta name="robots" content="index, follow" />
        <link rel="canonical" href="http://mysite.com/example" />
      </Helmet>
 
     </PrimaryLayout>
  </div>
);


```

### Contact Page



## Add Plugins

Gatsby Plugins can be found here: [Gatsby plugins](https://www.gatsbyjs.com/plugins/)

Plugins are added to gatsby-config.js after NPM package install.

Stop and restart server after adding a plugin.

Plugins that include the "source" in their name are used for sourcing data.

```
module.exports = {
  plugins: [
    {
      
    },
  ]
}

```

### Install Source File Plugin

A Gatsby source plugin for sourcing data into your Gatsby application from your local filesystem.

[Source File Plugin](https://www.gatsbyjs.com/plugins/gatsby-source-filesystem/?=)

**npm install gatsby-source-filesystem** 

```

module.exports = {
  plugins: [
     {
        resolve: `gatsby-source-filesystem`,
        options: {
        name: `src`,
        path: `${__dirname}/src/`,
      },
   },
  ]
}

```

You could test plugin by opening graphQL and querying the following

```

{
  allFile {
    nodes {
      relativePath
      prettySize
      extension
      birthTime
    }
  }
}

```

### Install SCSS

Provides drop-in support for Sass/SCSS stylesheets

[Sass Plugin](https://www.gatsbyjs.com/plugins/gatsby-plugin-sass/?=scss)


**npm install node-sass gatsby-plugin-sass**

Include the plugin in your gatsby-config.js file.

```
{ resolve: `gatsby-plugin-sass`}

```

Write your stylesheets in Sass/SCSS and require or import them as normal.

```

html {
  background-color: rebeccapurple;
  p {
    color: white;
  }
}

```

```

import "./src/index.scss"

```

### Install React Helmet

Used for SEO purposes.

[SEO Plugin](https://www.gatsbyjs.com/plugins/gatsby-plugin-react-helmet/)

**npm install gatsby-plugin-react-helmet react-helmet**

As we are not adding any options, the plugin module in gatsby-config.js would look something like this when its added

```

  plugins: [
     {
        resolve: `gatsby-source-filesystem`,
        options: {
        name: `src`,
        path: `${__dirname}/src/`,
      },
   },
     { resolve: `gatsby-plugin-react-helmet`}
  ]

```

import React Helmet to pages

```
import {Helmet} from 'react-helmet';

```

Create a Helmet

```

<Helmet>
    <meta charSet="utf-8" />
    <title>My Title</title>
    <meta name="description" content="Enter meta description" />
    <meta name="keywords" content="keywords, separated by comma" />
    <meta name="robots" content="index, follow" />
    <link rel="canonical" href="http://mysite.com/example" />
</Helmet>

```
### Transformer Remark

Use Markdown to add content

**npm install gatsby-transformer-remark**

```

 { resolve: `gatsby-transformer-remark`}

```



## Create Queries

Open gatsby-config.js

As a starting point enter the site meta data similar to below

```
module.exports = {
  /* Your site config here */
    siteMetadata {
      defaultTitle: title
      defaultDescription: description
      defaultImage: image
      url
      defaultKeywords:keywords
    }

```

Stop the server **CTRL + C**  

restart the server **gatsby develop**

Open graphQL.

Queries can be created with graphQL **http://localhost:8000/___graphql**

### Query in a Component

### Rendering Posts

### Creating Slugs for Posts

### Template Creation and Resolving

### Rendering Articles

## Optimise SEO

## Wordpress

## Gatsby Cheat Sheet

Install gatsby via the terminal **npm i -g gatsby-cli**

Create the gatsby project somewhere on system  **gatsby new hello-gatsby**

Open the project folder **cd hello-gatsby** 

open in Visual studio with **.code**

Install a starter theme: **gatsby new my-gatsby-project https://github.com/gatsbyjs/gatsby-starter-blog**

To install Bootstrap: **npm i bootstrap**

import Bootstrap CSS into index.js like this: **import 'bootstrap/dist/css/bootstrap.css';**

To install Font Awesome Icons: **npm i font-awesome**

import Font Awesome into index.js like this: **import 'font-awesome/css/font-awesome.css';**

Start the project **gatsby-develop**

Stop the development terminal **ctrl + C**

install NPM packages **npm install**

======================================================================================
Use the [simple react snippets]((https://marketplace.visualstudio.com/items?itemName=burkeholland.simple-react-snippets)) package in VisualStudio Code and use the below snippets/ shortcuts

**imr**	Import React

**imrc**	Import React / Component

**imrs**	Import React / useState

**imrse**	Import React / useState useEffect

**impt**	Import PropTypes

**impc**	Import React / PureComponent

**cc**	Class Component

**ccc**	Class Component With Constructor

**cpc**	Class Pure Component

**sfc**	Stateless Function Component

**cdm**	componentDidMount

**uef**	useEffect Hook

**cwm**	componentWillMount

**cwrp**	componentWillReceiveProps

**gds**	getDerivedStateFromProps

**scu**	shouldComponentUpdate

**cwu**	componentWillUpdate

**cdu**	componentDidUpdate

**cwu**	componentWillUpdate

**cdc**	componentDidCatch

**gsbu**	getSnapshotBeforeUpdate

**ss**	setState

**ssf**	Functional setState

**usf**	Declare a new state variable using State Hook

**ren**	render

**rprop**	Render Prop

**hoc**	Higher Order Component
