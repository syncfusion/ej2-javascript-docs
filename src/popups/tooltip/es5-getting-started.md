---
title: "ES5 Getting Started For Tooltip"
component: "Tooltip"
description: "Getting started with Tooltip in JavaScript (es5)."
---

# Getting Started with JavaScript(ES5)

The Essential JS 2 for JavaScript (global script) is an ES5 formatted pure JavaScript framework which can be directly used in latest web browsers.

## Component Initialization

The Essential JS 2 JavaScript components can be initialized by using either of the following ways.

* Using local script and style references in a HTML page.
* Using CDN link for script and style reference.

### Using local script and style references in a HTML page

**Step 1:** Create an app folder `myapp` for Essential JS 2 JavaScript components.

**Step 2:** You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2/confirm) build installed location.

**Syntax:**
> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.17/Essential JS 2/ej2-popups/dist/global/ej2-popups.min.js`
>
> Styles: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.17/Essential JS 2/ej2-popups/styles/material.css`

**Step 3:** Create a folder `myapp/resources` and copy/paste the global scripts and styles from the above installed location to `myapp/resources` location.

**Step 4:** Create a HTML page (index.html) in `myapp` location and add the Essentials JS 2 script and style references.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="resources/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 Tooltip's global script -->
            <script src="resources/ej2-popups.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>
```

**Step 5:** Now, add the `Tooltip` element and initiate the `Essential JS 2 Tooltip` component in the `index.html` by using following code

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <ink href="resources/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 Tooltip's global script -->
            <script src="resources/ej2-popups.min.js" type="text/javascript"></script>
       </head>
       <body>
            <!-- Add the HTML span element  -->
            <div id='container'>
                <div style="margin: 50px;">
                    <span id='target'>Show Tooltip</span>
                </div>
            </div>
            <script>
                // Initialize Essential JS 2 JavaScript Tooltip component
                var tooltip = new ej.popups.Tooltip({
                    width: '150px',
                    height: '40px',
                    content: 'Tooltip with specific width and height'
                });
                tooltip.appendTo('#target');
            </script>
       </body>
  </html>
```

**Step 6:** Now, run the `index.html` in web browser, it will render the **Essential JS 2 Tooltip** component.

### Using CDN link for script and style reference

**Step 1:** Create an app folder `myapp` for the Essential JS 2 JavaScript components.

**Step 2:** The Essential JS 2 component's global scripts and styles are already hosted in the below CDN link formats.

**Syntax:**
> Script: `https://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `https://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/styles/material.css`

**Example:**
> Script: [`https://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js`](https://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js)
>
> Styles: [`https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css`](https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css)
>
> We can also use [CRG](https://crg.syncfusion.com/) to generate combined component styles.

**Step 3:** Create a HTML page (index.html) in `myapp` location and add the CDN link references. Now, add the `Tooltip` element and initiate the `Essential JS 2 Tooltip` component in the index.html by using following code.

{% tab template="tooltip/es5-getting-started", sourceFiles="index.html" %}

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 Tooltip's global script -->
            <script src="//cdn.syncfusion.com/ej2/dist/ej2.min.js" type="text/javascript"></script>
       </head>
       <body>
           <!-- Add the HTML span element  -->
            <div id='container'>
                <div style="margin: 50px;">
                    <span id='target'>Show Tooltip</span>
                </div>
            </div>
            <script>
                //Initialize Essential JS 2 JavaScript Tooltip component
                var tooltip = new ej.popups.Tooltip({
                    width: '150px',
                    height: '40px',
                    content: 'Tooltip with specific width and height'
                });
                tooltip.appendTo('#target');
            </script>
       </body>
  </html>

```

{% endtab %}

**Step 4:** Now, run the `index.html` in web browser, it will render the `Essential JS 2 Tooltip` component.

## See Also

[Positioning Tooltip](./position/)

[Tooltip Open Mode](./open-mode/)

[Customize the Tooltip](./customization/)