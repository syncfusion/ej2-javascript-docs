---
title: "Frozen"
component: "TreeGrid"
description: "Learn how to freeze the tree grid columns at left or right side and how to freeze the tree grid rows at top."
---

# Frozen rows and columns

## Frozen rows and columns

Frozen rows and columns provides an option to make rows and columns always visible in the top and left side of the tree grid while scrolling.

To use frozen rows and columns support, inject the `Freeze` module in the tree grid.

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

You can use [`isFrozen`](../api/treegrid/column/#isfrozen) property to freeze selected columns in tree grid.

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

### Freeze direction

You can freeze the tree grid columns on the left or right side by using the [`column.freeze`](../api/treegrid/column/#freeze) property and the remaining columns will be movable. The tree grid will automatically move the columns to the left or right position based on the [`column.freeze`](../api/treegrid/column/#freeze) value.

Types of the [`column.freeze`](../api/treegrid/column/#freeze) directions:

* **`Left`**: Allows you to freeze the columns at the left.
* **`Right`**: Allows you to freeze the columns at the right.

In this demo, the **Task Name** column is frozen at the left and the **Priority** column is frozen at the right side of the content table.

{% tab template="treegrid/freezedirections", sourceFiles="index.ts,index.html",es5Template="freezedirection" %}

```typescript

import { TreeGrid, Freeze } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Freeze);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    height: 317,
    treeColumnIndex: 1,
    childMapping: 'subtasks',
    allowSelection: false,
    columns: [
                { field: 'taskID', headerText: 'Task ID', textAlign: 'Right', width: 90 },
                { field: 'taskName', headerText: 'Task Name', width: 230, freeze: 'Left' },
                { field: 'startDate', headerText: 'Start Date', width: 120, textAlign: 'Right',
                    type: 'date', format: { type: 'dateTime', format: 'dd/MM/yyyy' } },
                { field: 'endDate', headerText: 'End Date', width: 150, textAlign: 'Right',
                    type: 'date', format: { type: 'dateTime', format: 'dd/MM/yyyy' } },
                { field: 'duration', headerText: 'Duration', textAlign: 'Right', width: 110 },
                { field: 'progress', headerText: 'Progress', textAlign: 'Right', width: 120 },
                { field: 'priority', headerText: 'Priority', textAlign: 'Left', freeze: 'Right',  width: 120 },
                { field: 'approved', headerText: 'Approved', width: 110, textAlign: 'Left' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

> * Freeze Direction is not compatible with the [`isFrozen`](../api/treegrid/column/#isfrozen) and [`frozenColumns`](../api/treegrid/#frozencolumns) properties.

### Limitations of frozen tree grid

The following features are not supported in frozen rows and columns:

* Row Template
* Detail Template
* Cell Editing

Freeze Direction feature has the below limitations, along with the above mentioned limitations.

* Infinite scroll cache mode
* Freeze direction in the stacked header is not compatible with column reordering.

> You can refer to our [`JavaScript Tree Grid`](https://www.syncfusion.com/javascript-ui-controls/js-tree-grid) feature tour page for its groundbreaking feature representations. You can also explore our JavaScript tree grid example [`JavaScript Tree Grid example`](https://ej2.syncfusion.com/demos/#/material/tree-grid/treegrid-overview.html) to knows how to present and manipulate data.
