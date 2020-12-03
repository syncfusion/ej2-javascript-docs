---
title: "Template"
component: "Spinner"
description: "This section helps to learn how to set template to the spinner."
---

# Set the template to the Spinner

You can use custom templates on the Spinner instead of the default Spinner by specifying the template in the `setSpinner` method.

The following steps explains you on how to define template for Spinner.

* Import the `setSpinner` method from `ej2-popups` library into your `app.ts` as shown in below.

```typescript
import { setSpinner } from '@syncfusion/ej2-popups';
```

* Pass your custom template to the `setSpinner` method like as below.

```typescript
// Specify the template content to be displayed in the Spinner

setSpinner({ template: '<div style="width:100%;height:100%" class="custom-rolling"><div></div></div>'});
```

> You should set the template to the Spinner before creating the respective Essential JS 2 component. Also,until we replace `setSpinner` template, the further Essential JS 2 component rendering is created with given template only.

* Now, render the Essential JS 2 component. It's render the Spinner with the template specified in the `setSpinner` method.

> In the below sample, we have rendered the Grid component with custom Spinner using `setSpinner` method. You have to define the styles for the template in `styles.css`.

{% tab template="spinner/custom",sourceFiles="app.ts,index.html,styles.css", es5Template="custom" %}

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

// Specify the template content to be displayed in the Spinner

setSpinner({ template: '<div style="width:100%;height:100%" class="custom-rolling"><div></div></div>'});

let gridData2: Object[] = data.slice(0, 7);

// Spinner is rendered with template specified in the setSpinner method.

let grid2: Grid = new Grid({
    dataSource: gridData2,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'right', width: 120, type: 'number' },
        { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
        { field: 'Freight', headerText: 'Freight', textAlign: 'right', width: 120, format: 'C' },
        { field: 'OrderDate', headerText: 'Order Date', width: 140, format: 'yMd' }
    ]
});

grid2.appendTo('#Grid2');

grid2.hideSpinner = () => true;

```

{% endtab %}