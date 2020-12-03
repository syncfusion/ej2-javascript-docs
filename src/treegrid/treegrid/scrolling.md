---
title: "Scrolling"
component: "TreeGrid"
description: "Learn how to set width and height for TreeGrid content, display a scrollbar and make the TreeGrid responsive with a parent container."
---

# Scrolling

The scrollbar will be displayed in the treegrid when content exceeds the element [`width`](../api/treegrid/#width) or [`height`](../api/treegrid/#height). The vertical and horizontal scrollbars will be displayed based on the following criteria:

* The vertical scrollbar appears when the total height of rows present in the treegrid exceeds its element height.
* The horizontal scrollbar appears when the sum of columns width exceeds the treegrid element width.
* The [`height`](../api/treegrid/#height) and [`width`](../api/treegrid/#width) are used to set the treegrid height and width, respectively.

> The default value for [`height`](../api/treegrid/#height) and [`width`](../api/treegrid/#width) is `auto`.

## Set width and height

To specify the [`width`](../api/treegrid/#width) and [`height`](../api/treegrid/#height) of the scroller in the pixel, set the pixel value to a number.

{% tab template="treegrid/scrolling", es5Template="scroll" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    height: 315,
    width: 400,
    childMapping: 'subtasks',
    treeColumnIndex: 1,
    columns: [
                { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 180 },
                {
                    field: 'startDate', headerText: 'Start Date', width: 120, textAlign: 'Right', type: 'date',format: 'yMd'
                },
                { field: 'duration', headerText: 'Duration', width: 110, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Responsive with parent container

Specify the [`width`](../api/treegrid/#width) and [`height`](../api/treegrid/#height) as `100%` to make the treegrid element fill its parent container.
Setting the [`height`](../api/treegrid/#height) to `100%` requires the treegrid parent element to have explicit height.

{% tab template="treegrid/responsive-scrolling", sourceFiles="index.ts,index.html", es5Template="responsive" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    height: '100%',
    width: '100%',
    childMapping: 'subtasks',
    treeColumnIndex: 1,
    columns: [
                { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 180 },
                {
                    field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
                },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Scroll to selected row

You can scroll the treegrid content to the selected row position by using the [`rowSelected`](../api/treegrid/#rowselected) event.

{% tab template="treegrid/scroll-to-select-row", sourceFiles="index.ts,index.html",es5Template="scrollrow" %}

```typescript
import { TreeGrid, RowSelectEventArgs } from '@syncfusion/ej2-treegrid';
import { NumericTextBox } from '@syncfusion/ej2-inputs';
import { sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    height: '270',
    width: '100%',
    childMapping: 'subtasks',
    treeColumnIndex: 1,
    rowSelected: rowSelected,
    columns: [
                { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 180 },
                {
                    field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
                },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

let numeric: NumericTextBox = new NumericTextBox({
    width: 200,
    min: 0,
    showSpinButton: false,
    format: 'N',
    placeholder: 'Enter index to select a row',
    change: onchange
}, '#numeric');

function onchange(): void {
    treeGridObj.selectRow(parseInt(numeric.getText(), 10));
}

function rowSelected(args: RowSelectEventArgs) {
    let rowHeight: number = treeGridObj.getRows()[treeGridObj.getSelectedRowIndexes()[0]].scrollHeight;
    treeGridObj.getContent().children[0].scrollTop = rowHeight * treeGridObj.getSelectedRowIndexes()[0];
}

```

{% endtab %}

## Frozen rows and columns

Frozen rows and columns provides an option to make rows and columns always visible in the top and left side of the treegrid while scrolling.

To use frozen rows and columns support, inject the `Freeze` module in the treegrid.

In this demo, the [`frozenColumns`](../api/treegrid/#frozencolumns) is set as '2' and the [`frozenRows`](../api/treegrid/#frozenrows)
is set as '3'. Hence, the left two columns and top three rows are frozen.

{% tab template="treegrid/frozencolumns", sourceFiles="index.ts,index.html",es5Template="frozencolumn" %}

```typescript
import { TreeGrid, Freeze } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Freeze);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    height: 317,
    childMapping: 'subtasks',
    allowSelection: false,
    frozenRows: 3,
    frozenColumns: 2,
    treeColumnIndex: 1,
    columns: [
                { field: 'taskID', headerText: 'Task ID', textAlign: 'Right', width: 100 },
                { field: 'taskName', headerText: 'Task Name', width: 230 },
                { field: 'startDate', headerText: 'Start Date', width: 120, textAlign: 'Right',
                    type: 'date', format: { type: 'dateTime', format: 'dd/MM/yyyy' } },
                { field: 'endDate', headerText: 'End Date', width: 120, textAlign: 'Right',
                    type: 'date', format: { type: 'dateTime', format: 'dd/MM/yyyy' } },
                { field: 'duration', headerText: 'Duration', textAlign: 'Right', width: 110 },
                { field: 'progress', headerText: 'Progress', textAlign: 'Right', width: 120 },
                { field: 'priority', headerText: 'Priority', textAlign: 'Left', width: 120 },
                { field: 'approved', headerText: 'Approved', width: 110, textAlign: 'Left' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

### Freeze particular columns

You can use [`isFrozen`](../api/treegrid/column/#isfrozen) property to freeze selected columns in treegrid.

In this demo, the columns with field name `taskName` and `startDate` is frozen using
the `isFrozen` property.

{% tab template="treegrid/frozencolumns", sourceFiles="index.ts,index.html",es5Template="isfrozen" %}

```typescript
import { TreeGrid, Freeze } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Freeze);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    height: 317,
    childMapping: 'subtasks',
    allowSelection: false,
    columns: [
                { field: 'taskID', headerText: 'Task ID', textAlign: 'Right', width: 90 },
                { field: 'taskName', headerText: 'Task Name', width: 230, isFrozen: true },
                { field: 'startDate', headerText: 'Start Date', isFrozen: true, width: 120, textAlign: 'Right',
                    type: 'date', format: { type: 'dateTime', format: 'dd/MM/yyyy' } },
                { field: 'endDate', headerText: 'End Date', width: 150, textAlign: 'Right',
                    type: 'date', format: { type: 'dateTime', format: 'dd/MM/yyyy' } },
                { field: 'duration', headerText: 'Duration', textAlign: 'Right', width: 110 },
                { field: 'progress', headerText: 'Progress', textAlign: 'Right', width: 120 },
                { field: 'priority', headerText: 'Priority', textAlign: 'Left', width: 120 },
                { field: 'approved', headerText: 'Approved', width: 110, textAlign: 'Left' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

### Limitations

The following features are not supported in frozen rows and columns:

* Row Template
* Detail Template