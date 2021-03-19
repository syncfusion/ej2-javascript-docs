---
title: "Display custom tooltip for columns in grid"
component: "Grid"
description: "Learn how to display custom tooltip for columns in grid."
---

# Display custom tooltip for columns in grid

To display a custom ToolTip ([`EJ2 Tooltip`](../../../tooltip/getting-started)), you can render the Grid control inside the Tooltip component and set the target as “.e-rowcell”. The tooltip is displayed when hovering the grid cells.

Change the tooltip content for the grid cells by using the following code in the [`beforeRender`](../../../api/tooltip/#beforerender) event.

```typescript
function beforeRender(args) {
  // event triggered before render the tooltip on target element.
  tooltip.content = args.target.closest("td").innerText;
}

```

{% tab template="grid/custom-tooltip",es5Template="tooltip" %}

```typescript
import { Grid, QueryCellInfoEventArgs } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { Tooltip } from '@syncfusion/ej2-popups';

let tooltip: Tooltip = new Tooltip({
    target: ".e-rowcell", // set the target element to show the tooltip on hovering it
    beforeRender: beforeRender
  }, "#Tooltip");

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'ShipName', headerText: 'Ship Name', width: 140 },
        { field: 'ShipCity', headerText: 'Ship City', width: 100 },
    ],
    height: 315
});
grid.appendTo('#Grid');

function beforeRender(args) {
  // event triggered before render the tooltip on target element.
  tooltip.content = args.target.closest("td").innerText;
}

```

{% endtab %}
