---
title: "Selection"
component: "TreeGrid"
description: "Learn how to select rows and cells, use range selection, and use check box selection in the Essential JS 2 TreeGrid control."
---

# Selection

Selection provides an option to highlight a row or a cell. It can be done through simple mouse down or arrow keys. To disable selection in TreeGrid, set the [`allowSelection`](../api/treegrid/#allowselection) to false.

The treegrid supports two types of selection that can be set by using the [`selectionSettings.type`](../api/treegrid/selectionSettingsModel/#type). They are:

* **`Single`**: The `Single` value is set by default, and it only allows selection of a single row or a cell.
* **`Multiple`**: Allows you to select multiple rows or cells.
To perform the multi-selection, press and hold CTRL key and click the desired rows or cells. To select range of rows or cells, press and hold the SHIFT key and click the rows or cells.

{% tab template="treegrid/selection", es5Template="selection" %}

```typescript
import { TreeGrid, Selection } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    selectionSettings: { type: 'Multiple' },
    height: 270,
    treeColumnIndex: 1,
    columns: [
                { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 180 },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
                { field: 'progress', headerText: 'progress', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Selection Mode

TreeGrid supports three types of selection mode which can be set by using
[`selectionSettings.mode`](../api/treegrid/selectionSettings/#mode). They are:

* **`Row`** - The `row` value is set by default. Allows you to select rows only.
* **`Cell`** - Allows you to select cells only.
* **`Both`** - Allows you to select rows and cells at the same time.

{% tab template="treegrid/selection", es5Template="selectionmode" %}

```typescript
import { TreeGrid, Selection } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    selectionSettings: { mode: 'Both' },
    height: 315,
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
        { field: 'taskName', headerText: 'Task Name', width: 150 },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
        { field: 'progress', headerText: 'progress', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Cell selection

Cell Selection can be done through simple Mouse down or Arrow keys(up, down, left and right).

TreeGrid supports two types of cell selection mode which can be set by using
[`selectionSettings.cellSelectionMode`](../api/treegrid/selectionSettings/#cellselectionmode). They are:

* **`Flow`** - The `Flow` value is set by default.
Select range of cells between the start index and end index which includes in between cells of rows.
* **`Box`** - Select range of cells within the start and end column indexes which includes
in between cells of rows within the range.

{% tab template="treegrid/selection", es5Template="cellselection" %}

```typescript
import { TreeGrid, Selection } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    selectionSettings: { cellSelectionMode: 'Box', type: 'Multiple', mode: 'Cell' },
    height: 315,
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 150 },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
            { field: 'progress', headerText: 'progress', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Checkbox selection

Checkbox selection provides an option to select multiple treegrid records with help of checkbox in each row.

To render the checkbox in each treegrid row, you need to use checkbox column with type as `checkbox` using the  column [`type`](../api/treegrid/column/#type) property.

{% tab template="treegrid/selection", es5Template="checkboxselection" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 315,
    treeColumnIndex: 2,
    columns: [
            { type: 'checkbox', width: 60 },
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 150 },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
            { field: 'progress', headerText: 'progress', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

> * By default, selection is allowed by clicking a treegrid row or checkbox in that row. To allow selection only through checkbox, you can set the
[`selectionSettings.checkboxOnly`](../api/treegrid/selectionSettingsModel/#checkboxonly) property to true.
> * Selection can be persisted in all the operations using the [`selectionSettings.persistSelection`](../api/treegrid/selectionSettingsModel/#persistselection) property. For persisting selection on the treegrid, any one of the columns should be defined as a primary key using the [`columns.isPrimaryKey`](../api/treegrid/column/#isprimarykey) property.

### Checkbox selection Mode

In checkbox selection, selection can also be done by clicking on rows. This selection provides two types of Checkbox Selection mode which can be set by using the following API,
[`selectionSettings.checkboxMode`](../api/treegrid/selectionSettingsModel/#checkboxmode). The modes are;

* **`Default`**: This is the default value of the checkboxMode. In this mode, user can select multiple rows by clicking rows one by one.
* **`ResetOnRowClick`**: In ResetOnRowClick mode, when user clicks on a row it will reset previously selected row. Also you can perform multiple-selection in this mode by press
and hold CTRL key and click the desired rows. To select range of rows, press and hold the SHIFT key and click the rows.

{% tab template="treegrid/selection", es5Template="windowslikeselection" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 270,
    treeColumnIndex: 2,
    selectionSettings: {checkboxMode: 'ResetOnRowClick'},
    columns: [
            { type: 'checkbox', width: 60 },
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180 },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
            { field: 'progress', headerText: 'progress', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Toggle Selection

The Toggle selection allows to perform selection and unselection of the particular row or cell. To [`enable toggle`](../api/treegrid/selectionSettings/#enabletoggle) selection, set enableToggle property of the selectionSettings as true. If you click on the selected row or cell then it will be unselected and vice versa.

{% tab template="treegrid/selection", es5Template="toggleselection" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 270,
    treeColumnIndex: 1,
    selectionSettings: {enableToggle: true},
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180 },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
            { field: 'progress', headerText: 'progress', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

>If multi selection is enabled, then first click on any selected row (without pressing Ctrl key), it will clear the multi selection and in second click on the same row, it will be unselected.

## Select row at Initial rendering

To select a row at initial rendering, set the [`selectedRowIndex`](../api/treegrid/#selectedrowindex) value.

 {% tab template="treegrid/selection", es5Template="initselect" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 270,
    treeColumnIndex: 1,
    selectionSettings: { type: 'Multiple', mode: 'Both' },
    selectedRowIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
        { field: 'taskName', headerText: 'Task Name', width: 150 },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
        { field: 'progress', headerText: 'progress', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Get selected row indexes

You can get the selected row indexes by using the [`getSelectedRowIndexes`](../api/treegrid/#getselectedrowindexes) method.

{% tab template="treegrid/selection", es5Template="getindex" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { RowSelectEventArgs } from '@syncfusion/ej2-grids';
import { sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 270,
    treeColumnIndex: 1,
    selectionSettings: {type: 'Multiple'},
    rowSelected: rowSelected
    columns: [
        { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
        { field: 'taskName', headerText: 'Task Name', width: 150 },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
        { field: 'progress', headerText: 'progress', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

function rowSelected(args: RowSelectEventArgs) {
    let selectedrowindex: number[] = treeGridObj.getSelectedRowIndexes();  // get the selected row indexes.
    alert(selectedrowindex); // to alert the selected row indexes.
    let selectedrecords: Object[] = treeGridObj.getSelectedRecords();  // get the selected records.
}

```

{% endtab %}

## Touch interaction

When you tap a treegrid row on touchscreen device, the tapped row is selected.
It also shows a popup ![Multi Row selection](images/selection.jpg)  for multi-row selection.
To select multiple rows or cells, tap the popup![Multi Row or Cells](images/mselection.jpg)  and then tap the desired rows or cells.

> Multi-selection requires the selection [`type`](../api/treegrid/selectionSettings/#type) to be `multiple`.

The following screenshot represents a treegrid touch selection in the device.

<!-- markdownlint-disable MD033 -->
<img src="../images/touch-selection.png" alt="Touch interaction" style="width:320px;height: 620px">
<!-- markdownlint-enable MD033 -->

## Multiple Selection based on condition

You can select multiple treegrid rows based on condition by using the [`selectRows`](../api/treegrid/#selectrows) method.

In the following code, the rows which contains `taskID` value as `3` and `5` are selected at initial rendering.

{% tab template="treegrid/selection", es5Template="multiple" %}

```typescript
import { TreeGrid, Row, Column } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';


let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 270,
    treeColumnIndex: 1,
    selectionSettings: {type: 'Multiple'},
    dataBound: ()=>{
        let rowIndexes : number[]=[];
        treeGridObj.grid.dataSource.forEach((data,index)=>{
            if (data.taskID === 3 || data.taskID === 5){
                rowIndexes.push(index);
            }
        });
        treeGridObj.selectRows(rowIndexes);
     },
    columns: [
        { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
        { field: 'taskName', headerText: 'Task Name', width: 150 },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
        { field: 'progress', headerText: 'progress', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}
