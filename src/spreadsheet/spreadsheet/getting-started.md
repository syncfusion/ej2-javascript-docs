---
title: "Spreadsheet Getting Started ES-5"
component: "Spreadsheet"
description: "This section helps to learn how to create the Spreadsheet control in HTML5 JavaScript(ES-5) application with its basic features like selection, editing, formatting, importing and exporting to Excel."
---

# Getting Started

This section explains the steps to create a simple Essential JS 2 Spreadsheet control in a JavaScript application.

## Dependencies

The following list of dependencies is required to use the Spreadsheet control in your application:

```js
|-- @syncfusion/ej2-spreadsheet
   |-- @syncfusion/ej2-base
   |-- @syncfusion/ej2-dropdowns
   |-- @syncfusion/ej2-navigations
   |-- @syncfusion/ej2-grids

```

## Setup for local development

Refer to the following steps to setup your local environment.

**Step 1:** Create a root folder `myapp` for your application.

**Step 2:** Create `myapp/resources` folder to store local scripts and styles files.

**Step 3:** Create `myapp/index.js` and `myapp/index.html` files for initializing Essential JS 2 Spreadsheet control.

## Adding Syncfusion resources

The Essential JS 2 Spreadsheet control can be initialized by using any of the following two ways:

* Using local script and style.
* Using CDN link for script and style.

### Using local script and style

You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

After installing the Essential JS 2 product build, you can copy the Spreadsheet and its dependencies scripts and style file into the resources/scripts and resources/styles folder.

Refer to the following code to find Spreadsheet's script and style file location.

**Syntax:**

> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/17.2.0.34/Essential JS 2/ej2-spreadsheet/dist/global/ej2-spreadsheet.min.js`
>
> Styles: `C:/Program Files (x86)/Syncfusion/Essential Studio/17.2.0.34/Essential JS 2/ej2-spreadsheet/styles/material.css`

After copying the files, then you can refer the Spreadsheet's scripts and styles into the `index.html` file. The following html code example shows the minimal dependency of Spreadsheet.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Spreadsheet</title>
            <!-- Essential JS 2 Spreadsheet's dependents material theme -->
            <link href="resources/base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/inputs/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/splitbuttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/lists/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/navigations/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/dropdowns/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/dropdowns/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/grids/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 Spreadsheet's material theme -->
            <link href="resources/spreadsheet/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 Spreadsheet's dependents script -->
            <script src="resources/scripts/ej2-base.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-buttons.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-popups.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-splitbuttons.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-inputs.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-lists.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-data.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-dropdowns.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-navigations.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-excel-export.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-pdf-export.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-calenders.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-compression.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-file-utils.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-grids.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-svg-base.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-charts.min.js" type="text/javascript"></script>
            <!-- Essential JS 2 Spreadsheet global script -->
            <script src="resources/scripts/ej2-spreadsheet.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>

```

### Using CDN link for script and style

Using CDN link, you can directly refer the Spreadsheet control’s script and style into the `index.html`.

Refer to the Spreadsheet's CDN links as follows.

**Syntax:**

> Script: `https://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `https://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: [`http://cdn.syncfusion.com/ej2/ej2-spreadsheet/dist/global/ej2-spreadsheet.min.js`](http://cdn.syncfusion.com/ej2/ej2-spreadsheet/dist/global/ej2-spreadsheet.min.js)
>
> Styles: [`http://cdn.syncfusion.com/ej2/ej2-spreadsheet/styles/material.css`](http://cdn.syncfusion.com/ej2/ej2-spreadsheet/styles/material.css)

The following HTML code example shows the minimal dependency of Spreadsheet.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Spreadsheet</title>
            <!-- Essential JS 2 Spreadsheet's dependents material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-splitbuttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-lists/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-dropdowns/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-grids/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 Spreadsheet material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-spreadsheet/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 Spreadsheet's dependents script -->
            <script src=http://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js
            type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js
            type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-splitbuttons/dist/global/ej2-splitbuttons.min.js type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js
            type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-lists/dist/global/ej2-lists.min.js type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-data.min.js type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-dropdowns/dist/global/ej2-dropdowns.min.js
            type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js
            type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-excel-export/dist/global/ej2-excel-export.min.js type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-pdf-export/dist/global/ej2-pdf-export.min.js
            type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-calendars/dist/global/ej2-calendars.min.js
            type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-compression/dist/global/ej2-compression.min.js
            type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-file-utils/dist/global/ej2-file-utils.min.js
            type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-grids/dist/global/ej2-grids.min.js type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-svg-base/dist/global/ej2-svg-base.min.js
            type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-charts/dist/global/ej2-charts.min.js
            type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-spreadsheet/dist/global/ej2-spreadsheet.min.js
            type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>
```

## Add Spreadsheet control

Now, you can start adding Spreadsheet control in the application. For getting started, add a `div` element for Spreadsheet control in `index.html`. Then, refer the `index.js` file into the `index.html` file.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Spreadsheet</title>
            <!-- Essential JS 2 Spreadsheet's dependents material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-splitbuttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-lists/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-dropdowns/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-grids/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 Spreadsheet material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-spreadsheet/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 Spreadsheet's dependents script -->
            <script src=http://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js
            type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js
            type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-splitbuttons/dist/global/ej2-splitbuttons.min.js type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js
            type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-lists/dist/global/ej2-lists.min.js type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-data.min.js type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-dropdowns/dist/global/ej2-dropdowns.min.js
            type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js
            type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-excel-export/dist/global/ej2-excel-export.min.js type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-pdf-export/dist/global/ej2-pdf-export.min.js
            type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-calendars/dist/global/ej2-calendars.min.js
            type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-compression/dist/global/ej2-compression.min.js type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-file-utils/dist/global/ej2-file-utils.min.js
            type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-grids/dist/global/ej2-grids.min.js type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-svg-base/dist/global/ej2-svg-base.min.js
            type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-charts/dist/global/ej2-charts.min.js
            type="text/javascript"></script>
            <script src=http://cdn.syncfusion.com/ej2/ej2-spreadsheet/dist/global/ej2-spreadsheet.min.js
            type="text/javascript"></script>
       </head>
       <body>
           <!-- Add the HTML <div> element for Spreadsheet  -->
             <div id="element"></div>
             <script src="index.js" type="text/javascript"></script>
       </body>
  </html>

```

Place the following Spreadsheet code in the `index.js`.

```javascript

//Initialize the Spreadsheet control
var spreadsheet = new ej.spreadsheet.Spreadsheet();

//Render the initialized Spreadsheet
spreadsheet.appendTo('#element');

```

## Run the application

Now, run the `index.html` in web browser, it will render the Essential JS 2 Spreadsheet control.

Output will be displayed as follows.

{% tab template="spreadsheet/spreadsheet/es5-getting-started", sourceFiles="index.js,index.html", es5Template="index", iframeHeight="450px", isDefaultActive=true %}

```typescript
import { Spreadsheet } from '@syncfusion/ej2-spreadsheet';

// Initialize the Spreadsheet control
let spreadsheet: Spreadsheet = new Spreadsheet();

// Render initialized Spreadsheet
spreadsheet.appendTo('#element');
```

{% endtab %}

## See Also

* [Data Binding](./data-binding)
* [Open and Save](./open-save)