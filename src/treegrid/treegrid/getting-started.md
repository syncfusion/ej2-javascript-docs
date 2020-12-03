---
title: "Getting Started ES-5"
component: "TreeGrid"
description: "Learn how to create a TreeGrid and to enable the features like paging, filtering, sorting and in JavaScript(ES-5)"
---

# Getting Started

This section explains the steps required to create a simple Essential JS 2 TreeGrid and demonstrates the basic usage of the TreeGrid control in a JavaScript application.

## Dependencies

Following is the list of dependencies to use the TreeGrid with all features.

```javascript
|-- @syncfusion/ej2-treegrid
     |-- @syncfusion/ej2-treegrid
          |-- @syncfusion/ej2-base
          |-- @syncfusion/ej2-data
          |-- @syncfusion/ej2-buttons
          |-- @syncfusion/ej2-popups
          |-- @syncfusion/ej2-navigations
          |-- @syncfusion/ej2-dropdowns
          |-- @syncfusion/ej2-lists
          |-- @syncfusion/ej2-inputs
          |-- @syncfusion/ej2-splitbuttons
          |-- @syncfusion/ej2-calendars
          |-- @syncfusion/ej2-excel-export
          |-- @syncfusion/ej2-pdf-export
          |-- @syncfusion/ej2-file-utils
          |-- @syncfusion/ej2-compression
```

## Setup for local environment

Refer to the following steps to setup your local environment.

**Step 1:** Create a root folder `myapp` for your application.

**Step 2:** Create `myapp/resources` folder to store local scripts and styles files.

**Step 3:** Create `myapp/index.js` and `myapp/index.html` files for initializing Essential JS 2 TreeGrid control.

## Adding Syncfusion resources

The Essential JS 2 TreeGrid control can be initialized by using either of the following ways.

* Using local script and style.
* Using CDN link for script and style.

### Using local script and style

You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

After installing the Essential JS 2 product build, copy the TreeGrid and its dependencies scripts and style file into the `resources/scripts` and `resources/styles` folder.

Refer to the following code to find location TreeGrid's script and style file.

**Syntax:**

> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/16.4.40/Essential JS 2/ej2-treegrid/dist/global/ej2-treegrid.min.js`
>
> Styles: `C:/Program Files (x86)/Syncfusion/Essential Studio/16.4.40/Essential JS 2/ej2-treegrid/styles/material.css`

After copying the files, refer the TreeGrid's scripts and styles into the `index.html` file.
The following HTML code example shows the minimal dependency of TreeGrid.

```html

<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 TreeGrid</title>
            <!-- Essential JS 2 TreeGrid's dependent material theme -->
            <link href="resources/base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 material theme -->
            <link href="resources/treegrid/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 TreeGrid's dependent scripts -->
            <script src="resources/scripts/ej2-base.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-data.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-popups.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-grids.min.js" type="text/javascript"></script>
            <!-- Essential JS 2 TreeGrid's global script -->
            <script src="resources/scripts/ej2-treegrid.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>

```

### Using CDN link for script and style

Using CDN link, you can directly refer the TreeGrid control's script and style into the `index.html`.

Refer to the TreeGrid's CDN links as follows.

**Syntax:**

> Script: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: [`http://cdn.syncfusion.com/ej2/ej2-treegrid/dist/global/ej2-treegrid.min.js`](http://cdn.syncfusion.com/ej2/ej2-treegrid/dist/global/ej2-treegrid.min.js)
>
> Styles: [`http://cdn.syncfusion.com/ej2/ej2-treegrid/styles/material.css`](http://cdn.syncfusion.com/ej2/ej2-treegrid/styles/material.css)

The following HTML code example shows the minimal dependency of TreeGrid.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 TreeGrid</title>
            <!-- Essential JS 2 TreeGrid's dependent material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-grids/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-treegrid/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 TreeGrid's dependent script -->
            <script src="http://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-data.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-grids/dist/global/ej2-grids.min.js" type="text/javascript"></script>
            <!-- Essential JS 2 TreeGrid's global script -->
            <script src="http://cdn.syncfusion.com/ej2/ej2-treegrid/dist/global/ej2-treegrid.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>

```

## Adding TreeGrid control

Now, you can start adding TreeGrid control in the application. For getting started, add a `div` element for TreeGrid control in `index.html`. Then refer the `index.js` file into the `index.html` file.

In this document context, the `ej2.min.js` is used, which includes all the Essential JS 2 components and its dependent scripts.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 TreeGrid</title>
            <!-- Essential JS 2 TreeGrid's dependent material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-grids/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-treegrid/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 all script -->
            <script src="http://cdn.syncfusion.com/ej2/dist/ej2.min.js" type="text/javascript"></script>
       </head>
       <body>
           <!-- Add the HTML <div> element for TreeGrid  -->
             <div id="TreeGrid"></div>
             <script src="index.js" type="text/javascript"></script>
       </body>
  </html>

```

Place the following TreeGrid code in the `index.js`.

```javascript

var treeGridObj = ej.treegrid.TreeGrid();
treeGridObj.appendTo('#TreeGrid');

```

## Defining Row Data

Data for the TreeGrid control is bind by using the `dataSource` property. It accepts either an array of JavaScript object or `DataManager` instance.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 TreeGrid</title>
            <!-- Essential JS 2 TreeGrid's dependent material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="http://cdn.syncfusion.com/ej2/ej2-grids/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 material theme -->
            <link href="http://cdn.syncfusion.com/ej2/ej2-treegrid/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 all script -->
            <script src="http://cdn.syncfusion.com/ej2/dist/ej2.min.js" type="text/javascript"></script>
       </head>
       <body>
           <!-- Add the HTML <div> element for TreeGrid  -->
             <div id="TreeGrid"></div>
             <script src="index.js" type="text/javascript"></script>
       </body>
  </html>

```

Place the following TreeGrid code in the `index.js`.

```javascript
var sampleData = [
    {
        taskID: 1,
        taskName: 'Planning',
        startDate: new Date('02/03/2017'),
        duration: 5,
        subtasks: [
            { taskID: 2, taskName: 'Plan timeline', startDate: new Date('02/03/2017'), duration: 5 },
            { taskID: 3, taskName: 'Plan budget', startDate: new Date('02/03/2017'), duration: 5},
            { taskID: 4, taskName: 'Allocate resources', startDate: new Date('02/03/2017'), duration: 5},
            { taskID: 5, taskName: 'Planning complete', startDate: new Date('02/07/2017'), duration: 0}
        ]
    }];
var treeGridObj = ej.treegrid.TreeGrid({dataSource: sampleData});
treeGridObj.appendTo('#TreeGrid');

```

## Defining Columns

The TreeGrid has an option to define the columns as an array. In these columns, the following properties are used to customize the columns.

* The `field` has been added to map with a property name in an array of JavaScript objects.
* The `headerText` has been added to change the title of columns.
* The `textAlign` has been added to change the alignment of columns. By default, columns will be left aligned. To change the columns to right align, define `textAlign` to `Right`.
* Also, the another useful property, `format` has been used. Using this, you can format number and date values to standard or custom formats. Here, it is defined for the conversion of numeric values to currency.

Tree Column which is used to expand or collapse child rows is defined by using [`treeColumnIndex`](../api/treegrid/#treecolumnindex) property.

```javascript
var sampleData = [
    {
        taskID: 1,
        taskName: 'Planning',
        startDate: new Date('02/03/2017'),
        duration: 5,
        subtasks: [
            { taskID: 2, taskName: 'Plan timeline', startDate: new Date('02/03/2017'), duration: 5 },
            { taskID: 3, taskName: 'Plan budget', startDate: new Date('02/03/2017'), duration: 5},
            { taskID: 4, taskName: 'Allocate resources', startDate: new Date('02/03/2017'), duration: 5},
            { taskID: 5, taskName: 'Planning complete', startDate: new Date('02/07/2017'), duration: 0}
        ]
    }];
var treeGridObj = ej.treegrid.TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    treeColumnIndex: 1,
    columns: [
                { field: 'taskID', headerText: 'Task ID', width: 70, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 200, textAlign: 'Left' },
                {
                    field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
                },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ],
    height: 380
});
treeGridObj.appendTo('#TreeGrid');

```

In the above code example, the hierarchical data binding is represented in which the [`chilMapping`](../api/treegrid/#childmapping) property denotes the hierarchy relationship; whereas in self-referencing data binding [`idMapping`](../api/treegrid/#idmapping) and [`parentIdMapping`](../api/treegrid/#parentidmapping) denotes the hierarchy relationship.

## Module injection

To create a treegrid with additional features, inject the required modules. The following modules are used to extend TreeGrid's basic functionality.

* `Page`: Inject this module to use paging feature.
* `Sort`: Inject this module to use sorting feature.
* `Filter`: Inject this module to use filtering feature.
* `ExcelExport`: Inject this module to use Excel export feature.
* `PdfExport`: Inject this module to use PDF export feature.

These modules should be injected into the TreeGrid using the `ej.treegrid.TreeGrid.Inject` method.

> Additional feature modules are available [`here`](./module).

## Enable paging

The paging feature enables users to view the TreeGrid record in a paged view. It can be enabled by setting the  [`allowPaging`](../api/treegrid/#allowpaging-boolean) property to true. Inject the [`Page`](../api/treegrid/#pagermodule)
 module as follows. If the [`Page`](../api/treegrid/#pagermodule) module is not injected, the pager will not be rendered in the TreeGrid. The pager can be customized using the [`pageSettings`](../api/treegrid/#pagesettings) property.

In root-level paging mode, paging is based on the root-level rows only, i.e., it ignores the child row count and it can be enabled by using the [`pageSettings.pageSizeMode`](../api/treegrid/pageSettingsModel/#pagesizemode) property.

{% tab template="treegrid/tree-grid",es5Template="enablepaging", sourceFiles="index.js,index.html,es5-datasource.js" %}

```typescript
import { TreeGrid, Page } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';
TreeGrid.Inject(Page);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    treeColumnIndex: 1,
    allowPaging: true,
    pageSettings: { pageSize: 7 },
    columns: [
                { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
                {
                    field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
                },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Enable sorting

The sorting feature enables you to order the records. It can be enabled by setting the  [`allowSorting`](../api/treegrid/#allowsorting) property to true. Inject the [`Sort`](../api/treegrid/#sortmodule)
  module as follows. If the [`Sort`](../api/treegrid/#sortmodule) module is not injected, you cannot sort when a header is clicked. Sorting feature can be customized using the  [`sortSettings`](../api/treegrid/#sortsettings) property.

{% tab template="treegrid/tree-grid",es5Template="enablesort", sourceFiles="index.js,index.html,es5-datasource.js" %}

```typescript
import { TreeGrid, Sort, Page } from '@syncfusion/ej2-treegrid';
import { sortData } from './datasource.ts';

TreeGrid.Inject(Sort, Page);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sortData,
    childMapping: 'subtasks',
    treeColumnIndex: 1,
    allowSorting: true,
    sortSettings: { columns: [{ field: 'Category', direction: 'Ascending' }, { field: 'orderName', direction: 'Ascending' }] },
    allowPaging: true,
    columns: [
                { field: 'Category', headerText: 'Category', width: 150 },
                { field: 'orderName', headerText: 'Order Name', width: 170 },
                { field: 'orderDate', headerText: 'Order Date', width: 130, textAlign: 'Right', format: 'yMd',    type: 'date' },
                { field: 'price', headerText: 'Price', width: 100, format: 'C0', textAlign: 'Right' }
    ],
    height: 260
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Enable filtering

The filtering feature enables you to view the reduced amount of records based on the filter criteria. It can be enabled by setting the [`allowFiltering`](../api/treegrid/#allowfiltering) property to true.  The [`Filter`] module has to be injected as follows.
 If the [`Filter`] module is not injected,  filter bar will not be rendered in the TreeGrid. Filtering feature can be customized using the [`filterSettings`](../api/treegrid/#filtersettings) property.

By default, filtered records are shown along with its parent records. This behavior can be changed by using the [`filterSettings-hierarchyMode`](../api/treegrid/filterSettingsModel/#hierarchymode) property.

{% tab template="treegrid/tree-grid",es5Template="enablefilter", sourceFiles="index.js,index.html,es5-datasource.js" %}

```typescript
import { TreeGrid, Filter, Page, Sort } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Filter, Page, Sort);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    treeColumnIndex: 1,
    allowFiltering: true,
    columns: [
                { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
                {
                    field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
                },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ],
    pageSettings: {pageSize: 11},
    allowPaging: true,
    allowSorting: true
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Run the application

Now, run the `index.html` in the web browser, it will render the Essential JS 2 TreeGrid control.

Output will be displayed as follows.

{% tab template="treegrid/tree-grid", isDefaultActive=true,es5Template="started", sourceFiles="index.js,index.html,es5-datasource.js" %}

```typescript
import { TreeGrid, Filter, Page, Sort } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Filter, Page, Sort);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    treeColumnIndex: 1,
    allowFiltering: true,
    columns: [
                { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
                {
                    field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
                },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ],
    pageSettings: {pageSize: 11},
    allowPaging: true,
    allowSorting: true
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Deploy the application

The Essential JS 2 TreeGrid control features are segregated into individual feature-wise modules. The [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build and `CDN` scripts contains code for all features used in the TreeGrid. So, do not to use the `CDN` scripts in production. It is strongly recommended to generate script files to use in production using our **Custom Resource Generator**[`(CRG)`](https://crg.syncfusion.com/) for Essential JS 2. CRG allows you to generate the bundled script for the currently enabled features in TreeGrid.
