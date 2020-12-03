---
title: "Print"
component: "TreeGrid"
description: "Learn how to print TreeGrid content, set up pages for printing, perform external print, and print visible pages in the Essential JS 2 TreeGrid control."
---

# Print

To print the TreeGrid, use the [`print`](../api/treegrid/#print) method from treegrid instance. The print option can be displayed on the [`toolbar`](../api/treegrid/#toolbar) by adding the `print` toolbar item.

{% tab template="treegrid/print", es5Template="defaultprint" %}

```typescript
import { TreeGrid, Toolbar } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Toolbar);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    toolbar: ['Print'],
    height: 265,
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Page setup

Some of the print options cannot be configured through JavaScript code. So, you have to customize the layout, paper size, and margin options using the browser page setup dialog. Please refer to the following links to know more about the browser page setup:

* [`Chrome`](https://support.google.com/chrome/answer/1069693?hl=en&visit_id=1-636335333734668335-3165046395&rd=1)
* [`Firefox`](https://support.mozilla.org/en-US/kb/how-print-web-pages-firefox)
* [`Safari`](http://www.mintprintables.com/print-tips/adjust-margins-osx/)
* [`IE`](http://www.helpteaching.com/help/print/index.htm)

## Print using an external button

To print the treegrid from an external button, invoke the [`print`](../api/treegrid/#print) method.

{% tab template="treegrid/print-button",es5Template="external" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { Button } from '@syncfusion/ej2-buttons';
import { sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 265,
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

let printBtn: Button = new Button();
printBtn.appendTo('#print');

document.getElementById('print').addEventListener('click', () => {
    treeGridObj.print();
});

```

{% endtab %}

## Print the visible page

By default, the treegrid prints all the pages. To print the current page alone, set the [`printMode`](../api/treegrid/#printmode) to `CurrentPage`.

{% tab template="treegrid/print",es5Template="printpage" %}

```typescript
import { TreeGrid, Toolbar, Page } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Toolbar, Page);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    toolbar: ['Print'],
    printMode: 'CurrentPage',
    allowPaging: true,
    pageSettings: { pageSize: 8 },
    height: 220,
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Print large number of columns

By default, the browser uses A4 as page size option to print pages and to adapt the size of the page the browser print preview will auto-hide the overflowed contents. Hence treegrid with large number of columns will cut off to adapt the print page.

To show large number of columns when printing, adjust the scale option from print option panel based on your content size.

![Scale Option Setting](./images/print-preview.png)

## Show or Hide columns while Printing

You can show a hidden column or hide a visible column while printing the treegrid using [`toolbarClick`](../api/treegrid/#toolbarclick) and [`printComplete`](../api/treegrid/#printcomplete) events.

In the `toolbarClick` event, based on `args.item.text` as `Print`. We can show or hide columns by setting `column.visible` property to `true` or `false` respectively.

In the printComplete event, We have reversed the state back to the previous state.

In the below example, we have `Duration` as a hidden column in the treegrid. While printing, we have changed `Duration` to visible column and `StartDate` as hidden column.

{% tab template="treegrid/print", es5Template="showhide" %}

```typescript
import { TreeGrid, Toolbar } from '@syncfusion/ej2-treegrid';
import { Column } from '@syncfusion/ej2-grids';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Toolbar);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    toolbar: ['Print'],
    toolbarClick: function(args) {
        if (args.item.text === 'Print') {
            let cols: Column[] = this.grid.columns;
            for (var i = 0; i < cols.length; i++) {
                if (cols[i].field == "duration") {
                    cols[i].visible = true;
                }
                else if (cols[i].field == "startDate") {
                    cols[i].visible = false;
                }
            }
        }
    },
    printComplete: function(args) {
        let cols: Column[] = this.grid.columns;
        for (var i = 0; i < cols.length; i++) {
            if (cols[i].field == "duration") {
                cols[i].visible = false;
            }
            else if (cols[i].field == "StartDate") {
                    cols[i].visible = true;
            }
        }
    }
    height: 265,
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', visible: false, width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Limitations of Printing Large Data

When treegrid contains large number of data, printing all the data at once is not a best option for the browser performance. Because to render all the DOM elements in one page will produce performance issues in the browser. It leads to browser slow down or browser hang.

If printing of all the data is still needed, we suggest to Export the treegrid to `Excel` or `CSV` or `Pdf` and then print it from another non-web based application.