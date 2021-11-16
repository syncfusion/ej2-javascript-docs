---
title: "State Persistence"
component: "Grid"
description: "Learn how to persist the DataGrid state and model in the browser’s local storage."
---

# State Persistence

State persistence refers to the Grid's state maintained in the browser's [localStorage](https://www.w3schools.com/html/html5_webstorage.asp#) even if the browser is refreshed or if you move to the next page within the browser.
State persistence stores grid’s model object in the local storage when the [enablePersistence](../api/grid/#enablepersistence) is defined as true.

## Maintaining custom query in a persistent state

The grid does not maintain the query params after page load event when the [enablePersistence](../api/grid/#enablepersistence) is set to true. This is because the grid refreshes its query params for every page load. You can maintain the custom query params by resetting the [addParams](../api/data/query/#addparams) method in the [actionBegin](../api/grid/#actionbegin) event.

{% tab template="grid/grouping-event", es5Template="persistent" %}

```typescript
import { Grid, Filter, ActionEventArgs, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Filter, Page);

let grid: Grid = new Grid({
    dataSource: data,
    allowFiltering: true,
    allowPaging: true,
    enablePersistence: true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ],
    actionBegin: actionHandler,
    height: 230
});
grid.appendTo('#Grid');

function actionHandler(args: ActionEventArgs) {
    this.query.addParams('$filter', 'EmployeeID eq 1');
}

```

{% endtab %}

## Get or set localStorage value

If the [enablePersistence](../api/grid/#enablepersistence-) property is set to true, the grid property value is saved in the `window.localStorage` for reference. You can get/set the localStorage value by using the `getItem`/`setItem` method in the `window.localStorage`.

```typescript
//get the Grid model.
let value: string = window.localStorage.getItem('gridGrid'); //"gridGrid" is component name + component id.
let model: Object = JSON.parse(model);

```

```typescript
//set the Grid model.
window.localStorage.setItem('gridGrid', JSON.stringify(model)); //"gridGrid" is component name + component id.

```

## Restore initial Grid state

When the [enablePersistence](../api/grid/#enablepersistence) property is set to **true**, the Grid will keep its state even if the page is reloaded. In some cases, you may be required to retain the Grid in its initial state. The Grid will not retain its initial state now since the [`enablePersistence`](../api/grid/#enablepersistence) property has been enabled.

You can achieve this by destroying the grid after disabling the `enablePersistence` property and clearing the local storage data, as shown in the sample below.

{% tab template="grid/initial-grid", es5Template="initialgrid" %}

```typescript

import { Grid, Filter, ActionEventArgs, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Filter, Page);

let grid: Grid = new Grid({
    dataSource: data,
    enablePersistence: true,
    allowFiltering: true,
    allowPaging: true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ],
    height: 230
});
grid.appendTo('#Grid');

document.getElementById('restore').onclick = () => {
    grid.enablePersistence = false;
    window.localStorage.setItem("gridGrid", "");
    grid.destroy();
    //reloads the page
    location.reload();
}

```

{% endtab %}

## How to add a new column while using enablePersistence

The Grid columns can be persisted when the [enablePersistence](../api/grid/#enablepersistence) property is set to true. If you want to add the new columns with the existing persist state, you can use the Grid inbuilt method such as `column.push` and call the [refreshColumns()](../api/grid/#refreshcolumns) method for UI changes. Please refer to the following sample for more information.

{% tab template="grid/add-column", es5Template="addcolumn" %}

```typescript

import { Grid, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Page);

let grid: Grid = new Grid({
    dataSource: data,
    enablePersistence: true,
    allowPaging: true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ],
    height: 230
});
grid.appendTo('#Grid');

document.getElementById('add').onclick = () => {
    let obj = { field: "Freight", headerText: 'Freight', width: 120 }
    grid.columns.push(obj as any); //you can add the columns by using the Grid columns method
    grid.refreshColumns();
};

```

{% endtab %}

## How to prevent columns from persisting

When the [enablePersistence](../api/grid/#enablepersistence) property is set to true, the Grid properties such as [Grouping](../api/grid/groupSettingsModel/), [Paging](../api/grid/pageSettingsModel/), [Filtering](../api/grid/pageSettingsModel/), [Sorting](../api/grid/sortSettingsModel/), and [Columns](../api/grid/columnModel/) will persist. You can use the `addOnPersist` method to prevent these Grid properties from persisting.

The following example demonstrates how to prevent Grid columns from persisting. In the [dataBound](../api/grid/#databound) event of the Grid, you can override the `addOnPersist` method and remove the columns from the key list given for persistence.

>Note: When the `enablePersistence` property is set to true, the Grid features such as column template, column formatter, header text, and value accessor will not persist.

{% tab template="grid/column-prevent", es5Template="columnprevent" %}

```typescript

import { Grid, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Page);

let grid: Grid = new Grid({
    dataSource: data,
    enablePersistence: true,
    allowPaging: true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ],
    height: 230,
    dataBound: dataBound
});
grid.appendTo('#Grid');

function dataBound(args: any) {
    let cloned = this.addOnPersist;
    this.addOnPersist = function (key: any) {
        key = key.filter((item: string)  => item !== "columns");
        return cloned.call(this, key);
    };
}

document.getElementById('add').onclick = () => {
    let obj = { field: "Freight", headerText: 'Freight', width: 120 }
    grid.columns.push(obj as any); //you can add the columns by using the Grid columns method
    grid.refreshColumns();
};

document.getElementById('remove').onclick = () => {
    grid.columns.pop();
    grid.refreshColumns();
};

```

{% endtab %}

## Persist the Grid column template, header template, and headerText

By default, the Grid properties such as column template, header text, header template, column formatter, and value accessor will not persist when [enablePersistence](../api/grid/#enablepersistence) is set to true. Because the column template and header text can be customized at the application level.

If you wish to restore all these column properties, then you can achieve it by cloning the grid’s columns property using JavaScript Object’s assign method and storing this along with the persist data manually. While restoring the settings, this column object must be assigned to the grid’s columns property to restore the column settings as demonstrated in the following sample.

{% tab template="grid/column-persist", es5Template="column-persist" %}

```typescript

import { Grid, Page, Filter } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Filter, Page);

let grid: Grid = new Grid({
    dataSource: data,
    enablePersistence: true,
    allowFiltering: true,
    allowPaging: true,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150, headerTemplate: '#customertemplate' },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150, template: '#template'},
    ],
    height: 230
});
grid.appendTo('#Grid');

let savedProperties: any;
document.getElementById('restore').onclick = () => {
    savedProperties = JSON.parse(grid.getPersistData());
    var gridColumnsState = Object.assign([], grid.getColumns());
    savedProperties.columns.forEach((col: {
        field: any;
        headerText: any;
        template: any;
        headerTemplate: any;
    }) => {
        let headerText = gridColumnsState.find((colColumnsState) => colColumnsState.field === col.field)['headerText'];
        let colTemplate = gridColumnsState.find((colColumnsState) => colColumnsState.field === col.field)['template'];
        let headerTemplate = gridColumnsState.find((colColumnsState) => colColumnsState.field === col.field)['headerTemplate'];
        col.headerText = 'Text Changed';
        col.template = colTemplate;
        col.headerTemplate = headerTemplate; //likewise you can restore required column properties as per your wants.
    }
  );
    console.log(savedProperties);
    grid.setProperties(savedProperties);
};

```

{% endtab %}