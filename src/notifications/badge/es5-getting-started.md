---
title: "ES5 Getting Started For Badge"
component: "Badge"
description: "Getting started with Badge, a pure CSS component in JavaScript (es5)."
---

# Getting Started  with JavaScript(ES5)

The Essential JS 2 for JavaScript (global script) is an ES5 formatted pure JavaScript framework that can be directly used in latest web browsers.

## Component initialization

The Essential JS 2 JavaScript components can be initialized by using any of the following two ways:

* Using local script and style references in an HTML page.
* Using CDN link for script and style reference.

### Using local script and style references in an HTML page

**Step 1:** Create an app folder `myapp` for Essential JS 2 JavaScript components.

**Step 2:** You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2/confirm) build installed location.

**Syntax:**
> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.17/Essential JS 2/ej2-notifications/dist/global/ej2-notifications.min.js`
>
> Styles: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.17/Essential JS 2/ej2-notifications/styles/material.css`

**Step 3:** Create a folder `myapp/resources`, and copy and paste the global scripts and styles from the above installed location to `myapp/resources` location.

**Step 4:** Create an HTML page (index.html) in `myapp` location and add the Essentials JS 2 script and style references.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="resources/material.css" rel="stylesheet" type="text/css"/>
       </head>
       <body>
       </body>
  </html>
```

**Step 5:** Now, create a `span` element to apply the `Essential JS 2 Badge` component in the `index.html` by using following code.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="resources/material.css" rel="stylesheet" type="text/css"/>

       </head>
       <body>
            <!-- Add the HTML <span> element  -->
             <h1>Badge Component <span>New</span></h1>
       </body>
  </html>
```

**Step 6:** Now, run the `index.html` in web browser, it will render the **Essential JS 2 Badge** component.

### Using CDN link for script and style reference

**Step 1:** Create an app folder `myapp` for the Essential JS 2 JavaScript components.

**Step 2:** The Essential JS 2 component's global scripts and styles are already hosted in the following CDN link formats.

**Syntax:**
> Script: `https://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `https://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/styles/material.css`

**Example:**
> Styles: [`https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css`](http://cdn.syncfusion.com/ej2/ej2-base/styles/material.css)
>
>[`https://cdn.syncfusion.com/ej2/ej2-notifications/styles/material.css`](http://cdn.syncfusion.com/ej2/ej2-notifications/styles/material.css)

**Step 3:** Create an HTML page (index.html) in `myapp` location and add the CDN link references. Now, add the `span` element and initiate the `Essential JS 2 Badge` component in the index.html by using the following code.

{% tab template="badge/es5-getting-started", sourceFiles="index.html" %}

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-notifications/styles/material.css" rel="stylesheet" type="text/css"/>
       </head>
       <body>
           <!-- Add the HTML <span> element  -->
            <h1>Badge Component <span class="e-badge e-badge-primary">New</span></h1>
       </body>
  </html>

```

{% endtab %}

**Step 4:** Now, run the `index.html` in the web browser, it will render the `Essential JS 2 Badge` component.

## See Also

[Types of Badge](./types/)