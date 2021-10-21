---
title: "Open popup while focusing the dropdown edit cell"
component: "Grid"
description: "Learn how to open the popup list while focusing the dropdownedit cell."
---

# Open popup while focusing the dropdown edit cell

You can open the DropDownList popup while focusing the cell by invoking the [`showPopup`](../../api/drop-down-list/#showpopup) method inside the ['focus'](../../api/drop-down-list/#focus) event of DropDownList component.

In the below demo, we have bound the focus event for the edit DropDownList using the [`columns.edit.params`](../api/grid/column/#edit) property.

{% tab template="grid/grid",es5Template="openPopup" %}

```typescript
import { Grid, Edit, Toolbar, EJ2Intance } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Edit, Toolbar);

let grid: Grid = new Grid({
    dataSource: data,
    toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, isPrimaryKey: true },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'Freight', headerText: 'Freight', textAlign: 'Right', editType: 'numericedit', width: 120, format: 'C2' },
        { field: 'ShipCountry', headerText: 'Ship Country',  edit: { params: { focus: ddFocus } }, editType: 'dropdownedit', width: 150 }
    ],
    height: 265
});
grid.appendTo('#Grid');

function ddFocus(e: {event: MouseEvent | KeyboardEvent | TouchEvent}): void {
  ((e.event.target as HTMLElement).querySelector('.e-dropdownlist') as EJ2Intance).ej2_instances[0].showPopup();
}

```

{% endtab %}
