---
title: "State Persistence"
component: "Grid"
description: "Learn how to persist the DataGrid state and model in the browser’s local storage."
---

# State Persistence

State persistence refers to the Grid's state maintained in the browser's [`localStorage`](https://www.w3schools.com/html/html5_webstorage.asp#) even if the browser is refreshed or if you move to the next page within the browser.
State persistence stores grid’s model object in the local storage when the [`enablePersistence`](../api/grid/#enablepersistence) is defined as true.

## Maintaining custom query in a persistent state

The grid does not maintain the query params after page load event when the [`enablePersistence`](../api/grid/#enablepersistence) is set to true. This is because the grid refreshes its query params for every page load. You can maintain the custom query params by resetting the [`addParams`](../api/data/query/#addparams) method in the [`actionBegin`](../api/grid/#actionbegin) event.

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

If the [`enablePersistence`](../api/grid/#enablepersistence-) property is set to true, the grid property value is saved in the `window.localStorage` for reference. You can get/set the localStorage value by using the `getItem`/`setItem` method in the `window.localStorage`.

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

When the [`enablePersistence`](../api/grid/#enablepersistence) property is set to **true**, the Grid will keep its state even if the page is reloaded. In some cases, you may be required to retain the Grid in its initial state. The Grid will not retain its initial state now since the [`enablePersistence`](../api/grid/#enablepersistence) property has been enabled.

You can achieve this by destroying the grid after disabling the [`enablePersistence`](../api/grid/#enablepersistence) property and clearing the local storage data, as shown in the sample below.

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
