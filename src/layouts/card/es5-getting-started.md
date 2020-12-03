---
title: "Getting Started"
component: "Card"
description: "This section explains how to create a Card component in the JavaScript(ES-5) application with its basic features."
---

# Getting Started with JavaScript(ES5)

The Essential JS 2 for JavaScript (global script) is an ES5 formatted pure JavaScript framework that can be directly used in latest web browsers.

## Component initialization

The Essential JS 2 JavaScript components can be initialized by using any of the following two ways:

* Using local script and style references in an HTML page.
* Using CDN link for script and style reference.

### Using local script and style references in an HTML page

**Step 1:** Create an app folder `myapp` for Essential JS 2 JavaScript components.

**Step 2:** You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

**Syntax:**
> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.17/Essential JS 2/ej2-lists/dist/global/ej2-lists.min.js`
>
> Styles: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.17/Essential JS 2/ej2-layouts/styles/material.css`

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

**Step 5:** Now, create a `span` element to apply the `Essential JS 2 Card` component in the `index.html` by using following code.

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
             <span class='e-card'></span>
       </body>
  </html>
```

**Step 6:** Now, open the `index.html` in web browser, it will render the **Essential JS 2 Card** component.

### Using CDN link for script and style reference

**Step 1:** Create an app folder `myapp` for the Essential JS 2 JavaScript components.

**Step 2:** The Essential JS 2 component's global scripts and styles are already hosted in the following CDN link formats.

**Syntax:**
> Script: `https://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `https://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/styles/material.css`

**Example:**
> Styles: [`https://cdn.syncfusion.com/ej2/ej2-layouts/styles/material.css`](https://cdn.syncfusion.com/ej2/ej2-layouts/styles/material.css)

**Step 3:** Create an HTML page (index.html) in `myapp` location and add the CDN link references. Now, add the `span` element and initiate the `Essential JS 2 Card` component in the index.html by using the following code.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-layouts/styles/material.css" rel="stylesheet" type="text/css"/>
       </head>
       <body>
           <!-- Add the HTML <span> element  -->
            <span class='e-card'>This is simple Card</span>
       </body>
  </html>
```

**Step 4:** Now, open the `index.html` in the web browser, it will render the `Essential JS 2 Card` component.

> Need to refer dependency component styles and scripts as like above example. We can also use [CRG](https://crg.syncfusion.com/) to generate combined component styles.

## Adding a header and content

You can create Card with a header in a specific structure. For adding header you need to create a `div` element with `e-card-header` class added.

* You can include heading inside the Card header by adding a `div` element with `e-card-header-caption` class, and also content will be added by adding element with `e-card-content`. For detailed information, refer to the [Header and Content](./header-content/).

```html
    <div class = "e-card">                    --> Root Element
        <div class="e-card-header">           --> Root Header Element
            <div class="e-card-header-caption">    --> Root Heading Element
                <div class="e-card-header-title"></div>   --> Heading Title Element
            </div>
            <div class="e-card-content"></div>         --> Card content Element
        </div>
    </div>
```

* Now, open the html file in the web browser, it will render the `Card` component with header and content.

Output will be as follows:

{% tab template="card/es5-getting-started", isDefaultActive = "true", sourceFiles="index.html" %}

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
     <head>
          <title>Essential JS 2</title>
          <!-- Essential JS 2 material theme -->
          <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
          <link href="https://cdn.syncfusion.com/ej2/ej2-layouts/styles/material.css" rel="stylesheet" type="text/css"/>
     </head>
     <body>
          <div style="margin: 50px;">
               <!--element which is going to render the Card-->
               <div tabindex="0" class="e-card" id="basic">
                    <div class="e-card-header">
                         <div class="e-card-header-caption">
                              <div class="e-card-header-title">Advanced UWP</div>
                         </div>
                    </div>
                    <div class="e-card-content">
                         Communicating with Windows 10 and Other Apps, the second in a five-part series written by Succinctly series
                         author Matteo Pagani. To download the complete white paper, and other papers in the series, visit
                         the White Paper section of Syncfusion’s Technology Resource Portal.
                    </div>
               </div>
          </div>
     </body>
  </html>
```

{% endtab %}

## See Also

* [How to add a header and content](./header-content)