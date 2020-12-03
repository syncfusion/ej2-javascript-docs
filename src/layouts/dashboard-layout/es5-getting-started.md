---
title: "Dashboard Layout ES5 Getting Started"
component: "Dashboard Layout"
description: "Getting started with Dashboard Layout, a pure CSS component in JavaScript (es5)."
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

To generate the combined component styles, use Syncfusion [`CRG`](https://crg.syncfusion.com/) (Custom Resource Generator) in your application.

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

**Step 5:** Now, create a dashboard element to apply the `Essential JS 2 DashboardLayout` component in the `index.html` by using following code.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="resources/material.css" rel="stylesheet" type="text/css"/>
       </head>
       <body>
            <!-- Add the Dashboard element  -->
            <div id="dashboard_inline">
            <div id="one" class="e-panel" data-row="0" data-col="0" data-sizeX="1" data-sizeY="1">
                <div class="e-panel-container">
                   <div class="content">0</div>
                </div>
            </div>
            <div id="two" class="e-panel" data-row="0" data-col="1" data-sizeX="3" data-sizeY="2">
                <div class="e-panel-container">
                    <div class="content">1</div>
                </div>
            </div>
            <div id="three" class="e-panel" data-row="0" data-col="4" data-sizeX="1" data-sizeY="3">
                <div class="e-panel-container">
                    <div class="content">2</div>
                </div>
            </div>
            <div id="four" class="e-panel" data-row="1" data-col="0" data-sizeX="1" data-sizeY="1">
                <div class="e-panel-container">
                    <div class="content">3</div>
                </div>
            </div>
            <div id="five" class="e-panel" data-row="2" data-col="0" data-sizeX="2" data-sizeY="1">
                <div class="e-panel-container">
                  <div class="content">4</div>
                </div>
            </div>
            <div id="six" class="e-panel" data-row="2" data-col="2" data-sizeX="1" data-sizeY="1">
                <div class="e-panel-container">
                   <div class="content">5</div>
                </div>
            </div>
            <div id="seven" class="e-panel" data-row="2" data-col="3" data-sizeX="1" data-sizeY="1">
                <div class="e-panel-container">
                    <div class="content">6</div>
                </div>
       </body>
  </html>
```

**Step 6:** Now, run the `index.html` in web browser, it will render the **Essential JS 2 DashboardLayout** component.

### Using CDN link for script and style reference

The below example shows the rendering of DashboardLayout component using CDN link for script and style reference

* Setting the `panels` property using HTML attribute
* Setting the `panels` property using script

#### Setting the `panels` property using HTML attributes

**Step 1:** Create an app folder `myapp` for the Essential JS 2 JavaScript components.

**Step 2:** The Essential JS 2 component's global scripts and styles are already hosted in the following CDN link formats.

**Syntax:**
> Script: `https://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `https://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/styles/material.css`

**Example:**
> Styles: [`https://cdn.syncfusion.com/ej2/ej2-layouts/styles/material.css`](https://cdn.syncfusion.com/ej2/ej2-layouts/styles/material.css)

**Step 3:** Create an HTML page (index.html) in `myapp` location and add the CDN link references. Now, add the `dashboardlayout` element and initiate the `Essential JS 2 DashboardLayout` component in the index.html by using the following code.

{% tab template="dashboard-layout/es5-getting-started", isDefaultActive = "true", sourceFiles="index.html" %}

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
    <div id="element">
        <!-- Add the HTML <div> element  -->
        <div style="margin: 50px;">
            <!--element which is going to render the dashboardlayout-->
            <div id="dashboard_inline">
                <div id="one" class="e-panel" data-row="0" data-col="0" data-sizeX="1" data-sizeY="1">
                    <div class="e-panel-container">
                        <div class="content">0</div>
                    </div>
                </div>
                <div id="two" class="e-panel" data-row="0" data-col="1" data-sizeX="3" data-sizeY="2">
                    <div class="e-panel-container">
                        <div class="content">1</div>
                    </div>
                </div>
                <div id="three" class="e-panel" data-row="0" data-col="4" data-sizeX="1" data-sizeY="3">
                    <div class="e-panel-container">
                        <div class="content">2</div>
                    </div>
                </div>
                <div id="four" class="e-panel" data-row="1" data-col="0" data-sizeX="1" data-sizeY="1">
                    <div class="e-panel-container">
                        <div class="content">3</div>
                    </div>
                </div>
                <div id="five" class="e-panel" data-row="2" data-col="0" data-sizeX="2" data-sizeY="1">
                    <div class="e-panel-container">
                        <div class="content">4</div>
                    </div>
                </div>
                <div id="six" class="e-panel" data-row="2" data-col="2" data-sizeX="1" data-sizeY="1">
                    <div class="e-panel-container">
                        <div class="content">5</div>
                    </div>
                </div>
                <div id="seven" class="e-panel" data-row="2" data-col="3" data-sizeX="1" data-sizeY="1">
                    <div class="e-panel-container">
                        <div class="content">6</div>
                    </div>
                </div>
            </div>
            <script>
                //Initialize DashboardLayout component
                var dashboard = new ej.layouts.DashboardLayout({
                    cellSpacing: [10, 10],
                    columns: 5
                });
                //Render initialized DashboardLayout component
                dashboard.appendTo('#element');
            </script>
            <style>
                .content {
                    vertical-align: middle;
                    font-weight: 600;
                    font-size: 20px;
                    text-align: center;
                    line-height: 60px;
                }
                #dashboard_inline .e-panel {
                    transition:none !important;
                }
            </style>
</body>

</html>

```

{% endtab %}

**Step 4:** Now, run the `index.html` in the web browser, it will render the `Essential JS 2 DashboardLayout` component.

#### Setting the `panels` property using script

You can render the DashboardLayout component by using the **panels** property through script. Add the HTML div element for DashboardLayout into your `index.html` file.

`[src/index.html]`

```html
<body>
    <div style="margin: 50px;">
        <!--element which is going to render the DashboardLayout-->
        <div id="element">
        </div>
</body>

```

Now, render the panel property inside the `<script>` tag

```javascript

// initialize dashboardlayout component
var dashboard  = new ej.layouts.DashboardLayout ({
    cellSpacing: [10, 10],
    columns: 5,
    panels: [{ "sizeX": 1, "sizeY": 1, "row": 0, "col": 0, content:'<div class="content ">0</div>' },
    { "sizeX": 3, "sizeY": 2, "row": 0, "col": 1, content:'<div class="content">1</div>' },
    { "sizeX": 1, "sizeY": 3, "row": 0, "col": 4, content:'<div class="content">2</div>' },
    { "sizeX": 1, "sizeY": 1, "row": 1, "col": 0, content:'<div class="content">3</div>' },
    { "sizeX": 2, "sizeY": 1, "row": 2, "col": 0, content:'<div class="content">4</div>' },
    { "sizeX": 1, "sizeY": 1, "row": 2, "col": 2, content:'<div class="content">5</div>' },
    { "sizeX": 1, "sizeY": 1, "row": 2, "col": 3, content:'<div class="content">6</div>' }
    ]
});
// render initialized dashboardlayout
dashboard.appendTo('#element');

```

The following example shows a basic DashboardLayout by using the `panels` property.

{% tab template="dashboard-layout/es5-getting-started", isDefaultActive = "true", sourceFiles="index.html" %}

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
    <div>
        <!--element which is going to render the DashboardLayout-->
        <div id="element">
        </div>
        <script>
            //Initialize Dashboardlayout component
            var dashboard = new ej.layouts.DashboardLayout({
                cellSpacing: [10, 10],
                columns: 5,
                panels: [{ "sizeX": 1, "sizeY": 1, "row": 0, "col": 0, content: '<div class="content" style="line-height:60px">0</div>' },
                { "sizeX": 3, "sizeY": 2, "row": 0, "col": 1, content: '<div class="content" style="line-height:60px">1</div>' },
                { "sizeX": 1, "sizeY": 3, "row": 0, "col": 4, content: '<div class="content" style="line-height:60px">2</div>' },
                { "sizeX": 1, "sizeY": 1, "row": 1, "col": 0, content: '<div class="content" style="line-height:60px">3</div>' },
                { "sizeX": 2, "sizeY": 1, "row": 2, "col": 0, content: '<div class="content" style="line-height:60px">4</div>' },
                { "sizeX": 1, "sizeY": 1, "row": 2, "col": 2, content: '<div class="content" style="line-height:60px">5</div>' },
                { "sizeX": 1, "sizeY": 1, "row": 2, "col": 3, content: '<div class="content" style="line-height:60px">6</div>' }
                ]
            });
            //Render initialized Dashboardlayout component
            dashboard.appendTo('#element');
        </script>
        <style>
            .content {
                vertical-align: middle;
                font-weight: 600;
                font-size: 20px;
                text-align: center;
                line-height: 30px;
            }
            #element .e-panel {
                transition:none !important;
            }
        </style>
</body>

</html>

```

{% endtab %}
