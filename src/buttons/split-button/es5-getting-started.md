---
title: "SplitButton Javascript (es5) Getting Started"
component: "SplitButton"
description: "This section helps to learn how to create the splitbutton in HML5 JavaScript (ECMAScript 5) application with its basic features in step-by-step procedure."
---

# Getting Started  with JavaScript(ES5)

The Essential JS 2 for JavaScript (global script) is an ES5 formatted pure JavaScript framework which can be directly used in latest web browsers.

## Control Initialization

The Essential JS 2 JavaScript controls can be initialized by using either of the following ways.

* Using local script and style references in a HTML page.
* Using CDN link for script and style reference.

### Using local script and style references in a HTML page

**Step 1:** Create an app folder `quickstart` for getting started.

**Step 2:** You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

**Syntax:**
> Dependency Script: `**(installed location)**\Syncfusion\Essential Studio\JavaScript - EJ2\{RELEASE_VERSION}\Web (Essential JS 2)\JavaScript\{DEPENDENCY_PACKAGE_NAME}\dist\global\{DEPENDENCY_PACKAGE_NAME}.min.js`
>
> Control Script: `**(installed location)**\Syncfusion\Essential Studio\JavaScript - EJ2\{RELEASE_VERSION}\Web (Essential JS 2)\JavaScript\{PACKAGE_NAME}\dist\global\{PACKAGE_NAME}.min.js`
>
> Dependency Styles: `**(installed location)**\Syncfusion\Essential Studio\JavaScript - EJ2\{RELEASE_VERSION}\Web (Essential JS 2)\JavaScript\{DEPENDENCY_PACKAGE_NAME}\styles\material.css`
>
> Control Styles: `**(installed location)**\Syncfusion\Essential Studio\JavaScript - EJ2\{RELEASE_VERSION}\Web (Essential JS 2)\JavaScript\{PACKAGE_NAME}\styles\material.css`

**Example:**

> Dependency Script: `C:\Program Files (x86)\Syncfusion\Essential Studio\JavaScript - EJ2\16.3.0.17\Web (Essential JS 2)\JavaScript\ej2-base\dist\global\ej2-base.min.js`
>
> Control Script: `C:\Program Files (x86)\Syncfusion\Essential Studio\JavaScript - EJ2\16.3.0.17\Web (Essential JS 2)\JavaScript\ej2-splitbuttons\dist\global\ej2-splitbuttons.min.js`
>
> Dependency Styles: `C:\Program Files (x86)\Syncfusion\Essential Studio\JavaScript - EJ2\16.3.0.17\Web (Essential JS 2)\JavaScript\ej2-base\styles\material.css`
>
> Control Styles: `C:\Program Files (x86)\Syncfusion\Essential Studio\JavaScript - EJ2\16.3.0.17\Web (Essential JS 2)\JavaScript\ej2-splitbuttons\styles\material.css`

The below located script and style file contains all Syncfusion JavaScript (ES5) UI control resources in a single file.

> Scripts: `**(installed location)**\Syncfusion\Essential Studio\JavaScript - EJ2\{RELEASE_VERSION}\Web (Essential JS 2)\JavaScript\ej2\dist\ej2.min.js`
>
> Styles: `**(installed location)**\Syncfusion\Essential Studio\JavaScript - EJ2\{RELEASE_VERSION}\Web (Essential JS 2)\JavaScript\ej2\material.css`

The [`Custom Resource Generator (CRG)`](https://crg.syncfusion.com/) is an online web tool, which can be used to generate the custom script and styles for a set of specific controls. This web tool is useful to combine the required control scripts and styles in a single file.

**Step 3:** Create a folder `~/quickstart/resources` and copy/paste the global scripts and styles from the above installed location to `~/quickstart/resources/package` corresponding package location.

**Step 4:** Create a HTML page (index.html) in `~/quickstart/index.html` location and add the Essentials JS 2 script and style references.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 SplitButton's dependency style -->
            <link href="resources/base/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/buttons/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/popups/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 SplitButton's control style -->
            <link href="resources/splitbuttons/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 SplitButton's dependency global script -->
            <script src="resources/base/ej2-base.min.js" type="text/javascript"></script>
            <script src="resources/buttons/ej2-buttons.min.js" type="text/javascript"></script>
            <script src="resources/popups/ej2-popups.min.js" type="text/javascript"></script>

            <!-- Essential JS 2 SplitButton's control global script -->
            <script src="resources/splitbuttons/ej2-splitbuttons.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>
```

**Step 5:** Now, add the `SplitButton` element and initiate the `Essential JS 2 SplitButton` control in the `index.html` by using following code

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 SplitButton's dependency style -->
            <link href="resources/base/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/buttons/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/popups/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 SplitButton's control style -->
            <link href="resources/splitbuttons/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 SplitButton's dependency global script -->
            <script src="resources/base/ej2-base.min.js" type="text/javascript"></script>
            <script src="resources/buttons/ej2-buttons.min.js" type="text/javascript"></script>
            <script src="resources/popups/ej2-popups.min.js" type="text/javascript"></script>

            <!-- Essential JS 2 SplitButton's control global script -->
            <script src="resources/splitbuttons/ej2-splitbuttons.min.js" type="text/javascript"></script>
       </head>
       <body>
            <!--element which is going to render-->
            <button id='element'>Paste</button>
            <script>
                //Initialize action items.
                var items = [
                {
                  text: 'Cut'
                },
                {
                  text: 'Copy'
                },
                {
                  text: 'Paste'
                }];

                // initialize SplitButton control
                var splitBtn = new ej.splitbuttons.SplitButton({items: items});

                // Render initialized SplitButton.
                splitBtn.appendTo('#element');
            </script>
       </body>
  </html>
```

**Step 6:** Now, run the `index.html` in web browser, it will render the **Syncfusion JavaScript SplitButton** control.

### Using CDN link for script and style reference

**Step 1:** Create an app folder `quickstart` for getting started.

**Step 2:** The Essential JS 2 control's global scripts and styles are already hosted in the below CDN link formats.

**Syntax:**
> Dependency Script: `https://cdn.syncfusion.com/ej2/{DEPENDENCY_PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Control Script: `https://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Dependency Styles: `https://cdn.syncfusion.com/ej2/{DEPENDENCY_PACKAGE_NAME}/styles/material.css`
>
> Control Styles: `https://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/styles/material.css`

**Example:**
> Script: [`https://cdn.syncfusion.com/ej2/ej2-splitbuttons/dist/global/ej2-splitbuttons.min.js`](https://cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js)
>
> Styles: [`https://cdn.syncfusion.com/ej2/ej2-splitbuttons/styles/material.css`](http://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css)

**Step 3:** Create a HTML page (index.html) in `~/quickstart/index.html` location and add the CDN link references. Now, add the
`SplitButton` element and initiate the `Essential JS 2 SplitButton` control in the index.html by using following code.

{% tab template="split-button/es5-getting-started", sourceFiles="index.html" %}

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 SplitButton's dependency style -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 SplitButton's control style -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 SplitButton's dependency global script -->
           <script src="https://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
           <script src="https://cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
           <script src="https://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>

           <!-- Essential JS 2 SplitButton's control global script -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/dist/global/ej2-splitbuttons.min.js" type="text/javascript"></script>
       </head>
       <body>
            <!--element which is going to render-->
            <button id='element'>Paste</button>
            <script>
                ej.base.enableRipple(true);

                var items = [
                {
                  text: 'Cut'
                },
                {
                  text: 'Copy'
                },
                {
                  text: 'Paste'
                }];

                // initialize SplitButton control
                var splitBtn = new ej.splitbuttons.SplitButton({items: items});

                // Render initialized SplitButton.
                splitBtn.appendTo('#element');
            </script>
       </body>
  </html>

```

{% endtab %}

**Step 4:** Now, run the `index.html` in web browser, it will render the `Syncfusion JavaScript SplitButton` control.

## See Also

* [SplitButton with icons](./icons-and-separator#splitbutton-icons)
