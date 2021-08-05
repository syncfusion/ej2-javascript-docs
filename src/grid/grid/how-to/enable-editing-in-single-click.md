---
title: "Enable editing in single click"
component: "Grid"
description: "Learn how to enable single click editing in the Essential JS 2 DataGrid control."
---

# Enable editing in single click

## Normal Editing

You can make a row editable on a single click with `Normal` mode of editing in Grid, by using the [`startEdit`](../../api/grid/#startedit) and [`endEdit`](../../api/grid/#endedit) methods.

Bind the **mouseup** event for Grid and in the event handler call the [`startEdit`](../../api/grid/#startedit) and [`endEdit`](../../api/grid/#endedit), based on the clicked target element.

{% tab template="grid/grid", es5Template="single-click-inline-edit" %}

```typescript
import { Grid, Edit, IGrid, Toolbar } from '@syncfusion/ej2-grids';
import { MouseEventArgs } from '@syncfusion/ej2-base';
import { data } from './datasource.ts';

Grid.Inject(Edit, Toolbar);

let grid: Grid = new Grid({
    dataSource: data,
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
    toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, isPrimaryKey: true },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C2' },
        { field: 'ShipCountry', headerText: 'Ship Country', width: 150 }
    ],
    load: () => {
        let instance: IGrid = document.getElementById('Grid').ej2_instances[0];
        instance.element.addEventListener('mouseup', (e: MouseEventArgs) => {
            if (e.target.classList.contains("e-rowcell")) {
            if (instance.isEdit)
                instance.endEdit();
                let index: number = parseInt(e.target.getAttribute("Index"));
                instance.selectRow(index);
                instance.startEdit();
            }
        })
    }
    height: 220
});
grid.appendTo('#Grid');

```

{% endtab %}

### Open dropdown edit popup on single click

You can open the default dropdown edit popup with single click edit by focusing the dropdown element and calling the EJ2 dropdown list's showPopup(../../api/drop-down-list/#showpopup) method in the Grid's actionComplete(../../api/grid/#actioncomplete) event. In this demo we have used a global flag variable in the 'mouseup' event to ensure if the dropdown column is the clicked edit target.

{% tab template="grid/grid", es5Template="open-dropdown-popup" %}

```typescript
import { Grid, Edit, IGrid, Toolbar } from '@syncfusion/ej2-grids';
import { MouseEventArgs } from '@syncfusion/ej2-base';
import { data } from './datasource.ts';

Grid.Inject(Edit, Toolbar);

let isDropdown = false;

let grid: Grid = new Grid({
    dataSource: data,
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
    toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, isPrimaryKey: true },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C2' },
        { field: 'ShipCountry', headerText: 'Ship Country', editType: 'dropdownedit', width: 150 }
    ],
    actionComplete: onActionComplete,
    load: () => {
        let instance: IGrid = document.getElementById('Grid').ej2_instances[0];
        instance.element.addEventListener('mouseup', (e: MouseEventArgs) => {
            if (e.target.classList.contains("e-rowcell")) {
              if (instance.isEdit)
                  instance.endEdit();
              let rowInfo = instance.getRowInfo(e.target);
              if (rowInfo.column.field === "ShipCountry")
                  isDropdown = true;
              instance.selectRow(rowInfo.rowIndex);
              instance.startEdit();
            }
        })
    },
    height: 220
});
grid.appendTo('#Grid');

function onActionComplete(args) {
    if (args.requestType =="beginEdit" && isDropdown) {
        isDropdown = false;
        let dropdownObj = args.form.querySelector('.e-dropdownlist').ej2_instances[0];
        dropdownObj.element.focus();
        dropdownObj.showPopup();
    }
}


```

{% endtab %}

## Batch Editing

You can make a cell editable on a single click with `batch` mode of editing in Grid, by using the [`editCell`](../../api/grid/edit/#editcell) method.

Bind the **mouseup** event for Grid and in the event handler call the [`editCell`](../../api/grid/edit/#editcell) method, based on the clicked target element.

{% tab template="grid/grid", es5Template="single-click-batch-edit" %}

```typescript
import { Grid, Edit, IGrid, Toolbar } from '@syncfusion/ej2-grids';
import { MouseEventArgs } from '@syncfusion/ej2-base';
import { data } from './datasource.ts';

Grid.Inject(Edit, Toolbar);

let grid: Grid = new Grid({
    dataSource: data,
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Batch' },
    toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, isPrimaryKey: true },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C2' },
        { field: 'ShipCountry', headerText: 'Ship Country', width: 150 }
    ],
    load: () => {
        let instance: IGrid = document.getElementById('Grid').ej2_instances[0];
        instance.element.addEventListener('mouseup', (e: MouseEventArgs) => {
            if (e.target.classList.contains("e-rowcell")) {
                let index: number = parseInt(e.target.getAttribute("Index"));
                let colindex: number = parseInt(e.target.getAttribute("aria-colindex"));
                let field: string = instance.getColumns()[colindex].field;
                instance.editModule.editCell(index, field);
            }
        })
    }
    height: 220
});
grid.appendTo('#Grid');

```

{% endtab %}