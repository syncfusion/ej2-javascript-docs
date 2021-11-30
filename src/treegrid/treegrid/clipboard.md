---
title: "Clipboard"
component: "TreeGrid"
description: "Learn how to use the copy to clipboard functionality in the Essential JS 2 Tree Grid Control."
---

# Clipboard

The clipboard provides an option to copy selected rows or cells data into the clipboard.

The following list of keyboard shortcuts is supported in the Tree Grid to copy selected rows or cells data into the clipboard.

Interaction keys |Description
-----|-----
<kbd>Ctrl + C</kbd> |Copy selected rows or cells data into clipboard.
<kbd>Ctrl + Shift + H</kbd> |Copy selected rows or cells data with header into clipboard.

{% tab template="treegrid/clipboard", es5Template="clipboard" %}

```typescript
import { TreeGrid, Page, Selection } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Page, Selection);
let treegrid: TreeGrid = new TreeGrid(
    {
        dataSource: sampleData,
        childMapping: 'subtasks',
        treeColumnIndex: 1,
        allowSelection: true,
        allowPaging: true,
        pageSettings: { pageSize: 10 },
        selectionSettings: { type: 'Multiple', mode: 'Row' },
        columns: [
            { field: 'taskID', headerText: 'Task ID', width: 70, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 200, textAlign: 'Left' },
            { field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd' },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
            { field: 'progress', headerText: 'Progress', width: 80, textAlign: 'Right' },
        ],
        height: 260
    });
treegrid.appendTo('#TreeGrid');


```

{% endtab %}

## Copy to clipboard by external buttons

To copy selected rows or cells data into the clipboard with help of external buttons, you need to invoke the [`copy`](../api/treegrid/#copy) method.

{% tab template="treegrid/copy-method", es5Template="copymethod" %}

```typescript
import { TreeGrid, Page, Selection } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Page, Selection);
let treegrid: TreeGrid = new TreeGrid(
    {
        dataSource: sampleData,
        childMapping: 'subtasks',
        treeColumnIndex: 1,
        allowSelection: true,
        selectionSettings: { type: 'Multiple', mode: 'Row' },
        allowPaging: true,
        pageSettings: { pageSize: 10 },
        columns: [
            { field: 'taskID', headerText: 'Task ID', width: 70, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 200, textAlign: 'Left' },
            { field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd' },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
            { field: 'progress', headerText: 'Progress', width: 80, textAlign: 'Right' },
        ],
        height: 230
    });
treegrid.appendTo('#TreeGrid');

let copyBtn: Button = new Button();
copyBtn.appendTo('#copy');

document.getElementById('copy').addEventListener('click', () => {
    treegrid.copy();
});

let copyHeaderBtn: Button = new Button();
copyHeaderBtn.appendTo('#copyHeader');

document.getElementById('copyHeader').addEventListener('click', () => {
    treegrid.copy(true);
});

```

{% endtab %}

## Copy Hierarchy Modes

Tree Grid provides support for a set of copy modes with [`copyHierarchyMode`](../api/treegrid/#copyhierarchymode) property.
The below are the type of filter mode available in TreeGrid.

* **Parent** : This is the default copy hierarchy mode in Tree Grid. Clipboard value have the selected records with its parent records. If the selected records not have any parent record then the selected record will be in clipboard.

* **Child** : Clipboard value have the selected records with its child record. If the selected records do not have any child record then the selected records will be in clipboard.

* **Both** : Clipboard value have the selected records with its both parent and child record. If the selected records do not have any parent and child record then the selected records alone in clipboard.

* **None** : Only the Selected records will be in clipboard.

{% tab template="treegrid/hierarchy-copy",es5Template="hierarchy" %}

```typescript
import { TreeGrid, Page, Selection } from '@syncfusion/ej2-treegrid';
import { DropDownList, ChangeEventArgs } from '@syncfusion/ej2-dropdowns';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Page, Selection);
let treegrid: TreeGrid = new TreeGrid(
    {
        dataSource: sampleData,
        childMapping: 'subtasks',
        treeColumnIndex: 1,
        copyHierarchyMode: 'Parent',
        allowSelection: true,
        selectionSettings: { type: 'Multiple', mode: 'Row' },
        allowPaging: true,
        pageSettings: { pageSize: 10 },
        columns: [
            { field: 'taskID', headerText: 'Task ID', width: 70, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 200, textAlign: 'Left' },
            { field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd' },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
            { field: 'progress', headerText: 'Progress', width: 80, textAlign: 'Right' },
        ],
        height: 230
    });
treegrid.appendTo('#TreeGrid');

 let dropDownMode: DropDownList = new DropDownList({
    dataSource: [
        { id: 'Parent', mode: 'Parent' },
        { id: 'Child', mode: 'Child' },
        { id: 'Both', mode: 'Both' },
        { id: 'None', mode: 'None' },
    ],
    fields: { text: 'mode', value: 'id' },
    value: 'Parent',
    change: (e: ChangeEventArgs) => {
        let mode: any = <string>e.value;
        treeGridObj.copyHierarchyMode = mode;
    }
});
dropDownMode.appendTo('#mode');

```

{% endtab %}

### Limitations of Copy Functionality

* Only current view records will be available in copy clipboard.

## AutoFill

AutoFill Feature allows you to copy the data of selected cells and paste it to another cells by just dragging the autofill icon of the selected cells up to required cells. This feature is enabled by defining `enableAutoFill` property as true.

{% tab template="treegrid/clipboard", es5Template="auto" %}

```typescript
import { TreeGrid, Page, Selection, Edit, Toolbar } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Page, Selection, Edit, Toolbar );
let treegrid: TreeGrid = new TreeGrid(
    {
        dataSource: sampleData,
        childMapping: 'subtasks',
        treeColumnIndex: 1,
        enableAutoFill: true,
        enableHover: false,
        allowSelection: true,
        toolbar: ['Add', 'Update', 'Cancel'],
        selectionSettings: { type: 'Multiple', mode: 'Cell', cellSelectionMode: 'Box' },
        editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Batch' },
        allowPaging: true,
        pageSettings: { pageSize: 10 },
        columns: [
            { field: 'taskID', headerText: 'Task ID', isPrimaryKey: true, width: 70, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 200, textAlign: 'Left' },
            { field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd' },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
            { field: 'progress', headerText: 'Progress', width: 80, textAlign: 'Right' },
        ],
        height: 220
    });
treegrid.appendTo('#TreeGrid');

```

{% endtab %}

> * If `enableAutoFill` is set to true, then the autofill icon will be displayed on cell selection to copy cells.
> * It requires the selection `mode` to be `Cell`,  `cellSelectionMode` to be `Box` and also Batch Editing should be enabled.

### Limitations of AutoFill

* Since the string values are not parsed to number and date type, so when the selected string type cells are dragged to number type cells then it will display as **NaN**. For date type cells, when the selected string type cells are dragged to date type cells then it will display as an **empty cell**.
* Linear series and the sequential data generations are not supported in this autofill feature.

## Paste

You can able to copy the content of a cell or a group of cells by selecting the cells and pressing <kbd>Ctrl + C</kbd> shortcut key and paste it to another set of cells by selecting the cells and pressing <kbd>Ctrl + V</kbd> shortcut key.

{% tab template="treegrid/clipboard", es5Template="paste" %}

```typescript
import { TreeGrid, Page, Selection, Edit, Toolbar } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Page, Selection, Edit, Toolbar );
let treegrid: TreeGrid = new TreeGrid(
    {
        dataSource: sampleData,
        childMapping: 'subtasks',
        treeColumnIndex: 1,
        enableHover: false,
        allowSelection: true,
        toolbar: ['Add', 'Update', 'Cancel'],
        selectionSettings: { type: 'Multiple', mode: 'Cell', cellSelectionMode: 'Box' },
        editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Batch' },
        allowPaging: true,
        pageSettings: { pageSize: 10 },
        columns: [
            { field: 'taskID', headerText: 'Task ID', width: 70, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 200, textAlign: 'Left' },
            { field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd' },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
            { field: 'progress', headerText: 'Progress', width: 80, textAlign: 'Right' },
        ],
        height: 220
    });
treegrid.appendTo('#TreeGrid');

```

{% endtab %}

> To perform paste functionality, it requires the selection `mode` to be `Cell`,  `cellSelectionMode` to be `Box` and also Batch Editing should be enabled.

### Limitations of Paste Functionality

* Since the string values are not parsed to number and date type, so when the copied string type cells are pasted to number type cells then it will display as **NaN**. For date type cells, when the copied string format cells are pasted to date type cells then it will display as an **empty cell**.

> You can refer to our [`JavaScript Tree Grid`](https://www.syncfusion.com/javascript-ui-controls/js-tree-grid) feature tour page for its groundbreaking feature representations. You can also explore our JavaScript Tree Grid example [`JavaScript Tree Grid example`](https://ej2.syncfusion.com/demos/#/material/tree-grid/treegrid-overview.html) to knows how to present and manipulate data.