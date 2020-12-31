---
title: "JavaScript Kanban - Getting Started"
component: "Kanban"
description: "This article demonstrates how to create a simple Kanban and configure its available features."
---

# Getting Started

This section briefly explains how to create the **Kanban** component and configure its available functionalities in a JavaScript application.

## Dependencies

The following list of dependencies are required to use the Kanban component in your application:

```javascript
|-- @syncfusion/ej2-kanban
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-dropdowns
    |-- @syncfusion/ej2-icons
    |-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-layouts
    |-- @syncfusion/ej2-lists
    |-- @syncfusion/ej2-navigations
    |-- @syncfusion/ej2-popups
    |-- @syncfusion/ej2-splitbuttons
```

## Setup for local environment

Refer to the following steps to setup your local environment:

**Step 1:** Create a root folder `myapp` for your application.

**Step 2:** Create `myapp/resources` folder to store local scripts and styles files.

**Step 3:** Create `myapp/index.js` and `myapp/index.html` files for initializing Essential JS 2 Kanban control.

## Adding Syncfusion resources

The Essential JS 2 Kanban control can be initialized by using one of the following ways.

* Using local scripts and styles.
* Using CDN links for scripts and styles.

### Using local scripts and styles

You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

After installing the Essential JS 2 product build, you can copy the Kanban and its dependency scripts and style files into the `resources/scripts` and `resources/styles` folder respectively.

Refer to the following location from where the Kanban's script and styles can be referenced.

**Syntax:**

> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/17.4.39/Essential JS 2/ej2-kanban/dist/global/ej2-kanban.min.js`
>
> Styles: `C:/Program Files (x86)/Syncfusion/Essential Studio/17.4.39/Essential JS 2/ej2-kanban/styles/material.css`

After copying the files, you can refer the Kanban's scripts and styles into the `index.html` file.
The following HTML code example shows the dependency of Kanban.

```html

<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Kanban</title>
            <!-- Essential JS 2 Kanban's dependent material theme -->
            <link href="resources/base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/dropdowns/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/inputs/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/layouts/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/navigations/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 Kanban's material theme -->
            <link href="resources/kanban/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 Kanban's dependent scripts -->
            <script src="resources/scripts/ej2-base.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-buttons.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-data.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-dropdowns.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-inputs.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-splitbuttons.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-lists.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-popups.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-navigations.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-layouts.min.js" type="text/javascript"></script>
            <!-- Essential JS 2 Kanban's global script -->
            <script src="resources/scripts/ej2-kanban.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>

```

### Using CDN links for scripts and styles

Using CDN link, you can directly refer the Kanban's script and styles into the `index.html` file.

Refer to the Kanban's CDN links given as follows.

**Syntax:**

> Script: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: [`http://cdn.syncfusion.com/ej2/ej2-kanban/dist/global/ej2-kanban.min.js`](http://cdn.syncfusion.com/ej2/ej2-kanban/dist/global/ej2-kanban.min.js)
>
> Styles: [`http://cdn.syncfusion.com/ej2/ej2-kanban/styles/material.css`](http://cdn.syncfusion.com/ej2/ej2-kanban/styles/material.css)

The following HTML code example shows the dependency of Kanban with `ej2-kanban.min.js`.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Kanban</title>
            <!-- Essential JS 2 Kanban's dependent material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-dropdowns/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-layouts/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 Kanban's material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-kanban/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 Kanban's dependent script -->
            <script src="http://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-data.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-dropdown.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-layouts/dist/global/ej2-layouts.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-splitbuttons/dist/global/ej2-splitbuttons.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-lists/dist/global/ej2-lists.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js" type="text/javascript"></script>
            <!-- Essential JS 2 Kanban's global script -->
            <script src="http://cdn.syncfusion.com/ej2/ej2-kanban/dist/global/ej2-kanban.min.js" type="text/javascript"></script>
       </head>
       <body>
           <!-- Add the HTML <div> element for kanban  -->
             <div id="Kanban"></div>
             <script src="index.js" type="text/javascript"></script>
       </body>
  </html>

```

Place the following Kanban code in the `index.js` file.

```javascript
var kanbanObj = new ej.kanban.Kanban({
    columns: [
        { headerText: 'Backlog', keyField: 'Open' },
        { headerText: 'In Progress', keyField: 'InProgress' },
        { headerText: 'Testing', keyField: 'Testing' },
        { headerText: 'Done', keyField: 'Close' }
    ]
});
kanbanObj.appendTo('#Kanban');
```

## Initialize the Kanban

Now, you can add the Kanban control to the application. For getting started, add a `div` element for Kanban control in `index.html`. Then refer the `index.js` file into the `index.html` file.

In this document context, we are going to use `ej2.min.js`, which includes all the Essential JS 2 components and their dependent scripts.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Kanban</title>
            <!-- Essential JS 2 Kanban's dependent material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-dropdowns/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-layouts/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 Kanban's material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-kanban/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 all script -->
            <script src="http://cdn.syncfusion.com/ej2/dist/ej2.min.js" type="text/javascript"></script>
       </head>
       <body>
           <!-- Add the HTML <div> element for kanban  -->
             <div id="Kanban"></div>
             <script src="index.js" type="text/javascript"></script>
       </body>
  </html>

```

Place the following Kanban code in the `index.js` file.

```javascript
var kanbanObj = new ej.kanban.Kanban({
    columns: [
        { headerText: 'Backlog', keyField: 'Open' },
        { headerText: 'In Progress', keyField: 'InProgress' },
        { headerText: 'Testing', keyField: 'Testing' },
        { headerText: 'Done', keyField: 'Close' }
    ]
});
kanbanObj.appendTo('#Kanban');
```

{% tab template="kanban/getting-started-empty", es5Template="getting-started-empty", sourceFiles="index.ts,index.html,datasource.ts" %}

{% endtab %}

## Populating cards

To populate the empty Kanban with cards, define the local JSON data or remote data using the `dataSource` property. To define `dataSource`, the mandatory fields in JSON object should be relevant to `keyField`. In the following example, you can see the cards defined with default fields such as ID, Summary, and Status.

{% tab template="kanban/getting-started-key-field", es5Template="getting-started-key-field", sourceFiles="index.ts,index.html,datasource.ts" %}

{% endtab %}

## Enable swimlane

`Swimlane` can be enabled by mapping the fields `swimlaneSettings.keyField` to appropriate column name in dataSource. This enables the grouping of the cards based on the mapped column values.

{% tab template="kanban/getting-started-swimlane", es5Template="getting-started-swimlane", sourceFiles="index.ts,index.html,datasource.ts" %}

{% endtab %}