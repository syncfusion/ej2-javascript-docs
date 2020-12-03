---
title: "ContextMenu JavaScript (es5) Getting Started"
component: "ContextMenu"
description: "This section helps to learn how to create the contextmenu in HML5 JavaScript (ECMAScript 5) application with its basic features in step-by-step procedure."
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
> Control Script: `C:\Program Files (x86)\Syncfusion\Essential Studio\JavaScript - EJ2\16.3.0.17\Web (Essential JS 2)\JavaScript\ej2-navigations\dist\global\ej2-navigations.min.js`
>
> Dependency Styles: `C:\Program Files (x86)\Syncfusion\Essential Studio\JavaScript - EJ2\16.3.0.17\Web (Essential JS 2)\JavaScript\ej2-base\styles\material.css`
>
> Control Styles: `C:\Program Files (x86)\Syncfusion\Essential Studio\JavaScript - EJ2\16.3.0.17\Web (Essential JS 2)\JavaScript\ej2-navigations\styles\material.css`

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
          <!-- Essential JS 2 ContextMenu's dependent material theme -->
          <link href="resources/base/material.css" rel="stylesheet" type="text/css"/>
          <link href="resources/lists/material.css" rel="stylesheet" type="text/css"/>
          <link href="resources/popups/material.css" rel="stylesheet" type="text/css"/>

          <!-- Essential JS 2 ContextMenu's control material theme -->
          <link href="resources/navigations/material.css" rel="stylesheet" type="text/css"/>

          <!-- Essential JS 2 ContextMenu's dependent global script -->
          <script src="resources/base/ej2-base.min.js" type="text/javascript"></script>
          <script src="resources/data/ej2-data.min.js" type="text/javascript"></script>
          <script src="resources/lists/ej2-lists.min.js" type="text/javascript"></script>
          <script src="resources/popups/ej2-popups.min.js" type="text/javascript"></script>

          <!-- Essential JS 2 ContextMenu's control global script -->
          <script src="resources/navigations/ej2-navigations.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>
```

**Step 5:** Now, add the `ContextMenu` element and initiate the `Syncfusion JavaScript ContextMenu` control in the `index.html` by using following code

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
          <title>Essential JS 2</title>
          <!-- Essential JS 2 ContextMenu's dependent material theme -->
          <link href="resources/base/material.css" rel="stylesheet" type="text/css"/>
          <link href="resources/lists/material.css" rel="stylesheet" type="text/css"/>
          <link href="resources/popups/material.css" rel="stylesheet" type="text/css"/>

          <!-- Essential JS 2 ContextMenu's control material theme -->
          <link href="resources/navigations/material.css" rel="stylesheet" type="text/css"/>

          <!-- Essential JS 2 ContextMenu's dependent global script -->
          <script src="resources/base/ej2-base.min.js" type="text/javascript"></script>
          <script src="resources/data/ej2-data.min.js" type="text/javascript"></script>
          <script src="resources/lists/ej2-lists.min.js" type="text/javascript"></script>
          <script src="resources/popups/ej2-popups.min.js" type="text/javascript"></script>

          <!-- Essential JS 2 ContextMenu's control global script -->
          <script src="resources/navigations/ej2-navigations.min.js" type="text/javascript"></script>
       </head>
       <body>
            <!--target element-->
            <div id="target">Right click / Touch hold to open the ContextMenu</div>
            <!--element which is going to render-->
            <ul id="contextmenu"></ul>
            <script>
                var menuItems = [
                {
                  text: 'Cut'
                },
                {
                  text: 'Copy'
                },
                {
                  text: 'Paste'
                }];
                var menuOptions = {
                  target: '#target',
                  items: menuItems
                };

                // Initialize ContextMenu control.
                var menuObj = new ej.navigations.ContextMenu(menuOptions, '#contextmenu');
            </script>
       </body>
  </html>
```

**Step 6:** Now, run the `index.html` in web browser, it will render the **Syncfusion JavaScript ContextMenu** control.

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
> Script: [`https://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js`](http://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js)
>
> Styles: [`https://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css`](http://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css)

**Step 3:** Create a HTML page (index.html) in `~/quickstart/index.html` location and add the CDN link references. Now, add the `ContextMenu` element and initiate the `Syncfusion JavaScript ContextMenu` control in the index.html by using following code.

{% tab template="context-menu/es5-getting-started", sourceFiles="index.html,styles.css"%}

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 ContextMenu's dependent material theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-lists/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 ContextMenu's control material theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="styles.css" rel="stylesheet" />

            <!-- Essential JS 2 ContextMenu's dependent global script -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-lists/dist/global/ej2-lists.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>

            <!-- Essential JS 2 ContextMenu's control global script -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js" type="text/javascript"></script>
       </head>
       <body>
            <!--target element-->
            <div id="target">Right click / Touch hold to open the ContextMenu</div>
            <!--element which is going to render-->
            <ul id="contextmenu"></ul>
            <script>
                ej.base.enableRipple(true);

                var menuItems = [
                {
                  text: 'Cut'
                },
                {
                  text: 'Copy'
                },
                {
                  text: 'Paste'
                }];
                var menuOptions = {
                  target: '#target',
                  items: menuItems
                };

                // Initialize ContextMenu control.
                var menuObj = new ej.navigations.ContextMenu(menuOptions, '#contextmenu');
            </script>
       </body>
  </html>

```

{% endtab %}

**Step 4:** Now, run the `index.html` in web browser, it will render the `Syncfusion JavaScript ContextMenu` control.

## Rendering items with Separator

The Separators are the horizontal lines that are used to separate the menu items. You cannot select the separators. You
can enable separators to group the menu items using the [`separator`](../api/context-menu/menuItemModel#separator) property.
Cut, Copy, and Paste menu items are grouped using the `separator` property in the following sample.

{% tab template="context-menu/es5-getting-started", sourceFiles="index.html,styles.css" %}

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-lists/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="styles.css" rel="stylesheet" />

            <!-- Essential JS 2 ContextMenu's global script -->
             <script src="https://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
             <script src="https://cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
             <script src="https://cdn.syncfusion.com/ej2/ej2-lists/dist/global/ej2-lists.min.js" type="text/javascript"></script>
             <script src="https://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
             <script src="https://cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
             <script src="https://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js" type="text/javascript"></script>
       </head>
       <body>
           <!--target element-->
            <div id="target">Right click / Touch hold to open the ContextMenu</div>
            <!--element which is going to render-->
            <ul id="contextmenu"></ul>
            <script>
                ej.base.enableRipple(true);

                var menuItems = [
                {
                  text: 'Cut'
                },
                {
                  text: 'Copy'
                },
                {
                  text: 'Paste'
                },
                {
                  separator: true
                },
                {
                  text: 'Font'
                },
                {
                  text: 'Paragraph'
                }];
                var menuOptions = {
                  target: '#target',
                  items: menuItems
                };

                // Initialize ContextMenu control.
                var menuObj = new ej.navigations.ContextMenu(menuOptions, '#contextmenu');
            </script>
       </body>
  </html>

```

{% endtab %}

> The [`separator`](../api/context-menu/menuItemModel#separator) property `should not` be given along with
the other fields in the [`MenuItem`](../api/context-menu/menuItemModel).

## See Also

* [ContextMenu with icons](./icons-and-navigation#icons)
* [Multilevel nesting](./template-and-multilevel-nesting#multilevel-nesting)