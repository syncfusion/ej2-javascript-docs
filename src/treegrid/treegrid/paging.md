---
title: "Paging"
component: "TreeGrid"
description: "Learn how to add and customize the pager in the Essential JS 2 TreeGrid control."
---

# Paging

Paging provides an option to display TreeGrid data in page segments. To enable paging, set the [`allowPaging`](../api/treegrid/#allowpaging) to true. When paging is enabled, pager component renders at the bottom of the treegrid.
Paging options can be configured through the [`pageSettings`](../api/treegrid/#pagesettings).

To use paging, inject the [`Page`](../api/treegrid/#pagermodule) module in the treegrid.

{% tab template="treegrid/page",es5Template="paging" %}

```typescript
import { TreeGrid, Page } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Page);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowPaging: true,
    pageSettings: {pageSize: 7},
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
        { field: 'taskName', headerText: 'Task Name', width: 160 },
        {
            field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
        },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

> You can achieve better performance by using treegrid paging to fetch only a pre-defined number of records from the data source.

## Page Size Mode

Two behaviors are available in TreeGrid paging to display certain number of records in a current page. Following are the two types of [`pageSizeMode`](../api/treegrid/pageSettingsModel/#pagesizemode).

* **All** : This is the default mode. The number of records in a page is based on [`pageSize`](../api/treegrid/pageSettingsModel/#pagesize) property.
* **Root** : The number of root nodes or the 0th level records to be displayed per page is based on [`pageSize`](../api/treegrid/pageSettingsModel/#pagesize) property.

With [`pageSizeMode`](../api/treegrid/pageSettingsModel/#pagesizemode) property as `Root`, only the root level or the 0th level records are considered in records count.

{% tab template="treegrid/page",es5Template="rootpaging" %}

```typescript
import { TreeGrid, Page } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Page);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowPaging: true,
    height: 265,
    pageSettings: {pageSize: 2, pageSizeMode: 'Root'},
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
        { field: 'taskName', headerText: 'Task Name', width: 160 },
        {
            field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
        },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Template

You can use custom elements inside the pager instead of default elements.
The custom elements can be defined by using the [`template`](../api/treegrid/pageSettingsModel/#template) property.
Inside this template, you can access the [`currentPage`](../api/treegrid/pageSettingsModel/#currentpage), [`pageSize`](../api/treegrid/pageSettingsModel/#pagesize), [`pageCount`](../api/treegrid/pageSettingsModel/#pagecount), `totalPage` and `totalRecordCount` values.

{% tab template="treegrid/pager-template", sourceFiles="index.ts,index.html,index.css",es5Template="template" %}

```typescript
import { TreeGrid, Page, PageEventArgs } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';
import { NumericTextBox } from '@syncfusion/ej2-inputs';

TreeGrid.Inject(Page);

let flag: boolean = true;
let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowPaging: true,
    pageSettings: {pageSize: 6,  template: '#template'},
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
        { field: 'taskName', headerText: 'Task Name', width: 160 },
        {
            field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
        },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ],
    dataBound: () => {
        if (flag) {
            flag = false;
            updateTemplate();
        }
    },
    actionComplete: (args: PageEventArgs) => {
        if (args.requestType === 'paging') {
            updateTemplate();
        }
    }
});

treeGridObj.appendTo('#TreeGrid');

let updateTemplate: Function = () => {
    let numeric: NumericTextBox;
    this.numeric = new NumericTextBox({
        min: 1,
        max: 3,
        step: 1,
        width: 75,
        format: '###.##',
        change: (args) => {
            let value: number = args.value;
            treeGridObj.goToPage(value);
        }
    });
    this.numeric.appendTo('#currentPage');
};
let flag: boolean = true;

```

{% endtab %}

## Pager with Page Size Dropdown

The pager Dropdown allows you to change the number of records in the TreeGrid dynamically. It can be enabled by defining the [`pageSettings.pageSizes`](../api/treegrid/pageSettingsModel/#pagesizes) property as true.

```typescript
pageSettings: {pageSize: 7, pageSizes: true},
```

![Page size dropdown](images/pagesizes.png)

## How to render Pager at the Top of the TreeGrid

By default, Pager will be rendered at the bottom of the TreeGrid. You can also render the Pager at the top of the TreeGrid by using the `dataBound` event.

{% tab template="treegrid/page",es5Template="pagerattop" %}

```typescript
import { TreeGrid, Page } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Page);

let initialGridLoad: boolean = true;
let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowPaging: true,
    pageSettings: {pageSize: 7, pageSizes: true},
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
        { field: 'taskName', headerText: 'Task Name', width: 160 },
        {
            field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
        },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

treeGridObj.dataBound = () =>{
    if (initialGridLoad) {
        initialGridLoad = false;
        var pager = document.getElementsByClassName('e-gridpager');
        var topElement;
        if ( treeGridObj.toolbar) {
            topElement = document.getElementsByClassName('e-toolbar');
        } else {
            topElement = document.getElementsByClassName('e-gridheader');
        }
        topElement[0].before(pager[0]);
    }
};

```

{% endtab %}

> During the paging action, the pager component triggers the below three events.
> * The `created` event triggers when Pager is created.
> * The `click` event triggers when the numeric items in the pager is clicked.
> * The `dropDownChanged` event triggers when pageSize DropDownList value is selected.