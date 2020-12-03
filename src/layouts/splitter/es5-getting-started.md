---
title: "Splitter ES5 Getting Started"
component: "Splitter"
description: "Explains to get started with splitter control with its key features such as resizable,validation and nested splitter, etc."
---

# Getting Started with JavaScript(ES5)

The Essential JS 2 for JavaScript (global script) is an ES5 formatted pure JavaScript framework that can be directly used in latest web browsers.

## Component initialization

The Essential JS 2 JavaScript controls can be initialized by using any of the following two ways:

* Using local script and style references in an HTML page.
* Using CDN link for script and style reference.

### Using local script and style references in an HTML page

**Step 1:** Create an app folder `myapp` for Essential JS 2 JavaScript controls.

**Step 2:** You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

**Syntax:**
> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.17/Essential JS 2/ej2-layouts/dist/global/ej2-layouts.min.js`
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
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css" />
            <link href="https://cdn.syncfusion.com/ej2/ej2-layouts/styles/material.css" rel="stylesheet" type="text/css" />
            <!-- Essential JS 2 Dashboardlayout's global script -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-layouts/dist/global/ej2-layouts.min.js"
                type="text/javascript"></script>
        </head>
       <body>
       </body>
  </html>
```

**Step 5:** Now, create a `div` element to apply the `Essential JS 2 splitter` control in the `index.html` by using following code.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
        <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css" />
            <link href="https://cdn.syncfusion.com/ej2/ej2-layouts/styles/material.css" rel="stylesheet" type="text/css" />
            <!-- Essential JS 2 Dashboardlayout's global script -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-layouts/dist/global/ej2-layouts.min.js"
                type="text/javascript"></script>
        </head>
       <body>
          <div id='container'>
              <!--element which is render as splitter-->
              <div id="splitter">
                  <!--list of splitter panes-->
                  <div></div>
                  <div></div>
                  <div></div>
              </div>
          </div>
       </body>
  </html>
```

**Step 6:** Now, run the `index.html` in web browser, it will render the **Essential JS 2 splitter** control.

### Using CDN link for script and style reference

**Step 1:** Create an app folder `myapp` for the Essential JS 2 JavaScript controls.

**Step 2:** The Essential JS 2 component's global scripts and styles are already hosted in the following CDN link formats.

**Syntax:**
> Script: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/styles/material.css`

**Example:**
> Styles: [`http://cdn.syncfusion.com/ej2/ej2-layouts/styles/material.css`](http://cdn.syncfusion.com/ej2/ej2-layouts/styles/material.css)

**Step 3:** Create an HTML page (index.html) in `myapp` location and add the CDN link references. Now, add the `div` element and initiate the `Essential JS 2 splitter` control in the index.html by using the following code.

## Load content to the pane

You can load the pane contents in either HTML element or string types using [content](../api/splitter/paneProperties/#content) property.

For detailed information, refer to the [Pane Content](./pane-content/) section.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css" />
            <link href="https://cdn.syncfusion.com/ej2/ej2-layouts/styles/material.css" rel="stylesheet" type="text/css" />
            <!-- Essential JS 2 Dashboardlayout's global script -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-layouts/dist/global/ej2-layouts.min.js"
                type="text/javascript"></script>
        </head>
       <script>
        // Initialize splitter control
        var splitObj = new ej.layouts.Splitter({
            paneSettings: [
                // Content for Pane 1
                { content:'Left Pane' },

                // Content for Pane 2
                { content:'Middle Pane' },

                // Content for Pane 3
                { content:'Right Pane' }
            ],
            height: '250px'
        });
        // Render initialized splitter
        splitObj.appendTo('#splitter');
       </script>
       <body>
          <div id='container'>
              <!--element which is render as splitter-->
              <div id="splitter">
                  <!--list of splitter panes-->
                  <div></div>
                  <div></div>
                  <div></div>
              </div>
          </div>
       </body>
  </html>

```

{% tab template="splitter/getting-started", es5Template="getting-started", isDefaultActive =true %}

```typescript

import { Splitter } from '@syncfusion/ej2-layouts';

// Initialize splitter control
let splitObj: Splitter = new Splitter({
        paneSettings: [
            // Content for Pane 1
            { content:'Left Pane' },

            // Content for Pane 2
            { content:'Middle Pane' },

            // Content for Pane 3
            { content:'Right Pane' }
        ],
        height: '250px'
});

// Render initialized splitter
splitObj.appendTo('#splitter');


```

{% endtab %}

## See Also

* [Resizable split panes](./resizing/)
* [Collapsible panes](./expand-and-collapse/)
* [Construct different layouts using Splitter](./es5-different-layouts/)