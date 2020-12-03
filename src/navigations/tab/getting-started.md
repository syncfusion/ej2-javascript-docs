---
title: "Tab Getting Started"
component: "Tab"
description: "This section explains how to create a Tab component in an JavaScript(ES-5) application with its basic features."
---

# Getting Started  with JavaScript(ES5)

The Essential JS 2 for JavaScript (global script) is an ES5 formatted pure JavaScript framework which can be directly used in latest web browsers.

## Component Initialization

The Essential JS 2 JavaScript components can be initialized by using either of the following ways.

* Using local script and style references in a HTML page.
* Using CDN link for script and style reference.

### Using local script and style references in a HTML page

**Step 1:** Create an app folder `myapp` for Essential JS 2 JavaScript components.

**Step 2:** You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

**Syntax:**
> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-navigations/dist/global/ej2-navigations.min.js`
>
> Styles: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-navigations/styles/material.css`

**Step 3:** Create a folder `myapp/resources` and copy/paste the global scripts and styles from the above installed location to `myapp/resources` location.

**Step 4:** Create a HTML page (index.html) in `myapp` location and add the Essentials JS 2 script and style references.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="resources/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 Tab's global script -->
            <script src="resources/ej2-navigations.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>
```

**Step 5:** Now, add the `Tab` element and initiate the `Essential JS 2 Tab` component in the `index.html` by using following code

## Initialize the Tab using JSON items collection

The Tab can be rendered by defining a JSON array. The item is rendered with [`header`](../api/tab/tabItem#header) text and [`content`](../api/tab/tabItem#content) for each Tab using [`items`](../api/tab#items) property.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="resources/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 Tab's global script -->
            <script src="resources/ej2-navigations.min.js" type="text/javascript"></script>
       </head>
       <body>
            <!-- Add the HTML <div> element  -->
             <div id="element"></div>
            <script>
              var tabObj = new ej.navigations.Tab({
                  items: [
                      {
                          header: { 'text': 'Twitter' },
                          content: 'Twitter is an online social networking service that enables users to send and read short 140-character ' +
                          'messages called "tweets". Registered users can read and post tweets, but those who are unregistered can only read ' +
                          'them. Users access Twitter through the website interface, SMS or mobile device app Twitter Inc. is based in San ' +
                          'Francisco and has more than 25 offices around the world. Twitter was created in March 2006 by Jack Dorsey, ' +
                          'Evan Williams, Biz Stone, and Noah Glass and launched in July 2006. The service rapidly gained worldwide popularity, ' +
                          'with more than 100 million users posting 340 million tweets a day in 2012.The service also handled 1.6 billion ' +
                          'search queries per day.'
                      },
                      {
                          header: { 'text': 'Facebook' },
                          content: 'Facebook is an online social networking service headquartered in Menlo Park, California. Its website was ' +
                          'launched on February 4, 2004, by Mark Zuckerberg with his Harvard College roommates and fellow students Eduardo ' +
                          'Saverin, Andrew McCollum, Dustin Moskovitz and Chris Hughes.The founders had initially limited the website\'\s ' +
                          'membership to Harvard students, but later expanded it to colleges in the Boston area, the Ivy League, and Stanford ' +
                          'University. It gradually added support for students at various other universities and later to high-school students.'
                      },
                      {
                          header: { 'text': 'WhatsApp' },
                          content: 'WhatsApp Messenger is a proprietary cross-platform instant messaging client for smartphones that operates ' +
                          'under a subscription business model. It uses the Internet to send text messages, images, video, user location and ' +
                          'audio media messages to other users using standard cellular mobile numbers. As of February 2016, WhatsApp had a user ' +
                          'base of up to one billion,[10] making it the most globally popular messaging application. WhatsApp Inc., based in ' +
                          'Mountain View, California, was acquired by Facebook Inc. on February 19, 2014, for approximately US$19.3 billion.'
                      }
                  ]
                  });

              //Render initialized Tab component
              tabObj.appendTo('#element');
            </script>
       </body>
  </html>
```

**Step 6:** Now, run the `index.html` in web browser, it will render the **Essential JS 2 Tab** component.

### Using CDN link for script and style reference

**Step 1:** Create an app folder `myapp` for the Essential JS 2 JavaScript components.

**Step 2:** The Essential JS 2 component's global scripts and styles are already hosted in the below CDN link formats.

**Syntax:**
> Script: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/styles/material.css`

**Example:**
> Script: [`http://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js`](http://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js)
>
> Styles: [`http://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css`](http://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css)

**Step 3:** Create a HTML page (index.html) in `myapp` location and add the CDN link references. Now, add the `Tab` element and initiate the `Essential JS 2 Tab` component in the index.html by using following code.

{% tab template="tab/es5-getting-started", sourceFiles="index.html" %}

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 Tab's global script -->
            <script src="https://cdn.syncfusion.com/ej2/dist/ej2.min.js" type="text/javascript"></script>
       </head>
       <body>
           <!-- Add the HTML <div> element  -->
             <div id="element"></div>
            <script>
              var tabObj = new ej.navigations.Tab({
                  items: [
                      {
                          header: { 'text': 'Twitter' },
                          content: 'Twitter is an online social networking service that enables users to send and read short 140-character ' +
                          'messages called "tweets". Registered users can read and post tweets, but those who are unregistered can only read ' +
                          'them. Users access Twitter through the website interface, SMS or mobile device app Twitter Inc. is based in San ' +
                          'Francisco and has more than 25 offices around the world. Twitter was created in March 2006 by Jack Dorsey, ' +
                          'Evan Williams, Biz Stone, and Noah Glass and launched in July 2006. The service rapidly gained worldwide popularity, ' +
                          'with more than 100 million users posting 340 million tweets a day in 2012.The service also handled 1.6 billion ' +
                          'search queries per day.'
                      },
                      {
                          header: { 'text': 'Facebook' },
                          content: 'Facebook is an online social networking service headquartered in Menlo Park, California. Its website was ' +
                          'launched on February 4, 2004, by Mark Zuckerberg with his Harvard College roommates and fellow students Eduardo ' +
                          'Saverin, Andrew McCollum, Dustin Moskovitz and Chris Hughes.The founders had initially limited the website\'\s ' +
                          'membership to Harvard students, but later expanded it to colleges in the Boston area, the Ivy League, and Stanford ' +
                          'University. It gradually added support for students at various other universities and later to high-school students.'
                      },
                      {
                          header: { 'text': 'WhatsApp' },
                          content: 'WhatsApp Messenger is a proprietary cross-platform instant messaging client for smartphones that operates ' +
                          'under a subscription business model. It uses the Internet to send text messages, images, video, user location and ' +
                          'audio media messages to other users using standard cellular mobile numbers. As of February 2016, WhatsApp had a user ' +
                          'base of up to one billion,[10] making it the most globally popular messaging application. WhatsApp Inc., based in ' +
                          'Mountain View, California, was acquired by Facebook Inc. on February 19, 2014, for approximately US$19.3 billion.'
                      }
                  ]
                  });

              //Render initialized Tab component
              tabObj.appendTo('#element');
            </script>
       </body>
  </html>

```

{% endtab %}

**Step 4:** Now, run the `index.html` in web browser, it will render the `Essential JS 2 Tab` component.

## Initialize the Tab using HTML elements

The Tab component can be rendered based on the given HTML element using `id` as `target`.
Header section must be enclosed with in a wrapper element using `e-tab-header` class and corresponding content must be mapped with `e-content` class.
You need to follow the below structure of HTML elements to render the Tab,

```html

  <div id='tab_html_markup'>   --> Root Tab element
    <div class="e-tab-header">      --> Tab header
       <div>   --> Header Item
       </div>
    </div>
    <div class="e-content">      --> Tab content
       <div>   --> Content Item
       </div>
    </div>
  </div>

```

* Add the HTML template data with its id attribute and add it in your `index.html` file to initialize the Tab.

{% tab template="tab/es5-getting-started", sourceFiles="index.html" %}

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 Tab's global script -->
            <script src="https://cdn.syncfusion.com/ej2/dist/ej2.min.js" type="text/javascript"></script>
       </head>
       <body>
           <!-- Add the HTML <div> element  -->
             <div id="element">
                 <div class="e-tab-header">
                <div> Twitter </div>
                <div> Facebook </div>
                <div> WhatsApp </div>
            </div>
            <div class="e-content">
                <div>
                        Twitter is an online social networking service that enables users to send and read short 140-character messages called 'tweets'. Registered users can read and post tweets, but those who are unregistered can only read them. Users access Twitter through the website interface, SMS or mobile device app Twitter Inc. is based in San Francisco and has more than 25 offices around the world. Twitter was created in March 2006 by Jack Dorsey, Evan Williams, Biz Stone, and Noah Glass and launched in July 2006. The service rapidly gained worldwide popularity, with more than 100 million users posting 340 million tweets a day in 2012.The service also handled 1.6 billion search queries per day.
                </div>
                <div>
                        Facebook is an online social networking service headquartered in Menlo Park, California. Its website was launched on February 4, 2004, by Mark Zuckerberg with his Harvard College roommates and fellow students Eduardo Saverin, Andrew McCollum, Dustin Moskovitz and Chris Hughes.The founders had initially limited the website's membership to Harvard students, but later expanded it to colleges in the Boston area, the Ivy League, and Stanford University. It gradually added support for students at various other universities and later to high-school students.
                </div>
                <div>
                        WhatsApp Messenger is a proprietary cross-platform instant messaging client for smartphones that operates under a subscription business model. It uses the Internet to send text messages, images, video, user location and audio media messages to other users using standard cellular mobile numbers. As of February 2016, WhatsApp had a user base of up to one billion,[10] making it the most globally popular messaging application. WhatsApp Inc., based in Mountain View, California, was acquired by Facebook Inc. on February 19, 2014, for approximately US$19.3 billion.
                </div>
            </div>
             </div>
            <script>
              var tabObj = new ej.navigations.Tab();

              //Render initialized Tab component
              tabObj.appendTo('#element');
            </script>
       </body>
  </html>

```

{% endtab %}