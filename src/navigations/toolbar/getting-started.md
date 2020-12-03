---
title: "Toolbar Getting Started"
component: "Toolbar"
description: "This section explains how to create the Toolbar component in an JavaScript(ES-5) application with its basic features."
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

            <!-- Essential JS 2 Toolbar's global script -->
            <script src="resources/ej2-navigations.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>
```

**Step 5:** Now, add the `Toolbar` element and initiate the `Essential JS 2 Toolbar` component in the `index.html` by using following code

## Initialize the Toolbar with commands

The Toolbar can be rendered by defining an array of [`items`](../api/toolbar#items). An item is rendered with text by defining the default item type as a `Button`.
For more information about item configuration, refer to the [Item Configuration](./item-configuration/) section.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="resources/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 Toolbar's global script -->
            <script src="resources/ej2-navigations.min.js" type="text/javascript"></script>
       </head>
       <body>
            <!-- Add the HTML <div> element  -->
             <div id="element"></div>
            <script>
//Initialize Toolbar component

//Initialize Toolbar component

    var toolbar = new ej.navigations.Toolbar({
    items: [
      { text: 'Cut' },
      { text: 'Copy' },
      { text: 'Paste' },
      { type: 'Separator'},
      { text: 'Bold' },
      { text: 'Italic' },
      { text: 'Underline' },
    ]
    });

//Render initialized Toolbar component
    toolbar.appendTo('#element');

            </script>
       </body>
  </html>
```

**Step 6:** Now, run the `index.html` in web browser, it will render the **Essential JS 2 Toolbar** component.

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

**Step 3:** Create a HTML page (index.html) in `myapp` location and add the CDN link references. Now, add the `Toolbar` element and initiate the `Essential JS 2 Toolbar` component in the index.html by using following code.

{% tab template="toolbar/es5-getting-started", sourceFiles="index.html" %}

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

            <!-- Essential JS 2 global script -->
            <script src="https://cdn.syncfusion.com/ej2/dist/ej2.min.js" type="text/javascript"></script>
       </head>
       <body>
           <!-- Add the HTML <div> element  -->
             <div id="element"></div>
            <script>
//Initialize Toolbar component

    var toolbar = new ej.navigations.Toolbar({
    items: [
      { text: 'Cut' },
      { text: 'Copy' },
      { text: 'Paste' },
      { type: 'Separator'},
      { text: 'Bold' },
      { text: 'Italic' },
      { text: 'Underline' },
    ]
    });

//Render initialized Toolbar component
    toolbar.appendTo('#element');

            </script>
       </body>
  </html>

```

{% endtab %}

**Step 4:** Now, run the `index.html` in web browser, it will render the `Essential JS 2 Toolbar` component.

## See Also

* [Initialize the toolbar using HTML elements](../toolbar/template-configuration)