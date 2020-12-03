---
title: "Types"
component: "Spinner"
description: "This section helps to learn how to change the type of the spinner."
---

# Change the type of the Spinner

By default, the Spinner is loaded in the applicable Essential JS 2 component based on the theme imported into the page. Based on the theme, the type is set to the Spinner.
The available types are:
* Material
* Fabric
* Bootstrap

You can change the Essential JS 2 component spinner type by passing the type of the spinner as parameter to the `setSpinner` method like as below.

```typescript
// Specify the type of the Spinner to be displayed

setSpinner({ type: 'Bootstrap'});
```

> After Essential JS 2 component creation only, you can change the Essential JS 2 component spinner type.

{% tab template="spinner/default",sourceFiles="app.ts,index.html,styles.css", es5Template="default" %}

```typescript

import { createSpinner, setSpinner , showSpinner } from '@syncfusion/ej2-popups';
import { Grid } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

let gridData: Object[] = data.slice(0, 7);

// By default, Spinner is rendered with specified theme inside the Grid component.

let grid: Grid = new Grid({
    dataSource: gridData,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'right', width: 120, type: 'number' },
        { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
        { field: 'Freight', headerText: 'Freight', textAlign: 'right', width: 120, format: 'C' },
        { field: 'OrderDate', headerText: 'Order Date', width: 140, format: 'yMd' }
    ]
});

grid.appendTo('#Grid');

grid.hideSpinner = () => true;

// Specify the type of the Spinner to be displayed in the Grid.

setSpinner({ type: 'Bootstrap'});

```

{% endtab %}