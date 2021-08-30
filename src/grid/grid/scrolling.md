---
title: "Scrolling"
component: "Grid"
description: "Learn how to set width and height for DataGrid content, display a scrollbar, freeze rows and columns, and make the DataGrid responsive with a parent container."
---

# Scrolling

 The scrollbar will be displayed in the grid when content exceeds the element [`width`](../api/grid/#width) or [`height`](../api/grid/#height). The vertical and horizontal scrollbars will be displayed based on the following criteria:

* The vertical scrollbar appears when the total height of rows present in the grid exceeds its element height.
* The horizontal scrollbar appears when the sum of columns width exceeds the grid element width.
* The [`height`](../api/grid/#height) and [`width`](../api/grid/#width) are used to set the grid height and width, respectively.

> The default value for [`height`](../api/grid/#height) and [`width`](../api/grid/#width) is `auto`.

## Set width and height

To specify the [`width`](../api/grid/#width) and [`height`](../api/grid/#height) of the scroller in the pixel, set the pixel value to a number.

{% tab template="grid/scroller", es5Template="scroll" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: data,
    height: 315,
    width: 400,
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'EmployeeID', headerText: 'Employee ID', textAlign: 'Right', width: 120 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipCountry', headerText: 'Ship Country', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ]
});
grid.appendTo('#Grid');

```

{% endtab %}

## Responsive with parent container

Specify the [`width`](../api/grid/#width) and [`height`](../api/grid/#height) as `100%` to make the grid element fill its parent container.
Setting the [`height`](../api/grid/#height) to `100%` requires the grid parent element to have explicit height.

{% tab template="grid/scroll-parent", sourceFiles="index.ts,index.html", es5Template="responsive" %}

```typescript
import { Grid, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Page);

let grid: Grid = new Grid({
    dataSource: data,
    columns: [
                { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120, type: 'number' },
                { field: 'CustomerID', width: 140, headerText: 'Customer ID', type: 'string' },
                { field: 'Freight', headerText: 'Freight', textAlign: 'Right', width: 120, format: 'C' },
                { field: 'OrderDate', headerText: 'Order Date', width: 140, format: 'yMd' }
    ],
    height: '100%',
    allowPaging: true
});

grid.appendTo('#Grid');

```

{% endtab %}

## Scroll to selected row

You can scroll the grid content to the selected row position by using the [`rowSelected`](../api/grid/#rowselected) event.

{% tab template="grid/scroll-to-select-row", sourceFiles="index.ts,index.html",es5Template="scrollrow" %}

```typescript
import { Grid, RowSelectEventArgs } from '@syncfusion/ej2-grids';
import { NumericTextBox } from '@syncfusion/ej2-inputs';
import { data } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: data,
    height: '270',
    width: '100%',
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'EmployeeID', headerText: 'Employee ID', textAlign: 'Right', width: 120 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ],
    rowSelected: rowSelected
});
grid.appendTo('#Grid');

let numeric: NumericTextBox = new NumericTextBox({
    width: 200,
    min: 0,
    showSpinButton: false,
    format: 'N',
    placeholder: 'Enter index to select a row',
    change: onchange
}, '#numeric');

function onchange(): void {
    grid.selectionModule.selectRow(parseInt(numeric.getText(), 10));
}

function rowSelected(args: RowSelectEventArgs) {
    let rowHeight: number = grid.getRows()[grid.getSelectedRowIndexes()[0]].scrollHeight;
    grid.getContent().children[0].scrollTop = rowHeight * grid.getSelectedRowIndexes()[0];
}

```

{% endtab %}

## Hide the scrollbar when the content is not overflown

You can hide the scrollbar of Grid content by using the [`hideScroll`](../api/grid/#hidescroll) method when the content doesn't overflow its parent element.

In the following sample, we have invoked the [`hideScroll`](../api/grid/#hidescroll) method inside the [`dataBound`](../api/grid/#databound) event.  

{% tab template="grid/scroller", sourceFiles="index.ts,index.html",es5Template="hidescroll" %}

```typescript
import { Grid } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

let grid: Grid = new Grid({
    dataSource: data.slice(0, 5),
    height: '315',
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'EmployeeID', headerText: 'Employee ID', textAlign: 'Right', width: 120 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ],
    dataBound:() => {
        grid.hideScroll();
    }
    });
grid.appendTo('#Grid');
```

{% endtab %}
