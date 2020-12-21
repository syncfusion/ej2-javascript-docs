---
title: "Immutable"
component: "Grid"
description: "Learn how to use immutable data in the Essential JS 2 DataGrid control."
---

# Immutable Mode

The immutable mode optimizes the Grid re-rendering performance by using the object reference and [`deep compare`](https://dmitripavlutin.com/how-to-compare-objects-in-javascript/#4-deep-equality) concept. When performing the Grid actions, it will only re-render the modified or newly added rows and prevent the re-rendering of the unchanged rows.

To enable this feature, you have to set the [`enableImmutableMode`](../api/grid/#enableImmutableMode) property as **true**.

>* This feature uses the primary key value for data comparison. So, you need to provide the [`isPrimaryKey`](../api/grid/column/#isprimarykey) column.

{% tab template="grid/immutable",es5Template="control" %}

```typescript
import { Grid, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';
import { Button } from '@syncfusion/ej2-buttons';

Grid.Inject(Page);

let immutableStart;
let normalStart;
let primaryKey = 0;
let immutableInit = true;
let init = true;

let immutableGrid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    pageSettings: { pageSize: 50 },
    enableImmutableMode: true,
    beforeDataBound: () => {
        immutableStart = new Date().getTime();
    },
    dataBound: ()=> {
        let val = immutableInit ? '' : new Date().getTime() - immutableStart;
        document.getElementById('immutableDelete').innerHTML = 'Immutable rendering Time: ' + "<b>" + val + "</b>" + '<b>ms</b>';
        immutableStart = 0; immutableInit = false;
    },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', isPrimaryKey: true, textAlign: 'Right', width: 120 },
        { field: 'ProductName', headerText: 'Product Name', width: 160 },
        { field: 'ProductID', headerText: 'Product ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'CustomerName', headerText: 'Customer Name', width: 160 }
    ],
    height: 240
});
immutableGrid.appendTo('#immutable');

document.getElementById('delete').addEventListener('click', function(e) {
    immutableGrid.dataSource.splice(0, 5);
    normalGrid.setProperties({ dataSource: immutableGrid.dataSource });
    immutableGrid.setProperties({ dataSource: immutableGrid.dataSource });
});

document.getElementById('addtop').addEventListener('click', function(e) {
    let addedRecords = [
            {'OrderID': ++primaryKey, 'ProductName': 'Chai', 'ProductID': 'Sasquatch Ale', 'CustomerID': 'QUEDE', 'CustomerName': 'Yoshi Tannamuri'},
            {'OrderID': ++primaryKey, 'ProductName': 'Georg Pipps', 'ProductID': 'Valkoinen suklaa', 'CustomerID': 'RATTC', 'CustomerName': 'Martín Sommer'},
            {'OrderID': ++primaryKey, 'ProductName': 'Yoshi Tannamuri', 'ProductID': 'Gula Malacca', 'CustomerID': 'COMMI', 'CustomerName': 'Ann Devon'},
            {'OrderID': ++primaryKey, 'ProductName': 'Palle Ibsen', 'ProductID': 'Rogede sild', 'CustomerID': 'RATTC', 'CustomerName': 'Paula Wilson'},
            {'OrderID': ++primaryKey, 'ProductName': 'Francisco Chang', 'ProductID': 'Mascarpone Fabioli', 'CustomerID': 'ROMEY', 'CustomerName': 'Jose Pavarotti'}
        ]
    let aData = addedRecords.concat(immutableGrid.dataSource);
    normalGrid.setProperties({ dataSource: aData });
    immutableGrid.setProperties({ dataSource: aData });
});

document.getElementById('addbottom').addEventListener('click', function(e) {
    let addedRecords = [
            {'OrderID': ++primaryKey, 'ProductName': 'Chai', 'ProductID': 'Sasquatch Ale', 'CustomerID': 'QUEDE', 'CustomerName': 'Yoshi Tannamuri'},
            {'OrderID': ++primaryKey, 'ProductName': 'Georg Pipps', 'ProductID': 'Valkoinen suklaa', 'CustomerID': 'RATTC', 'CustomerName': 'Martín Sommer'},
            {'OrderID': ++primaryKey, 'ProductName': 'Yoshi Tannamuri', 'ProductID': 'Gula Malacca', 'CustomerID': 'COMMI', 'CustomerName': 'Ann Devon'},
            {'OrderID': ++primaryKey, 'ProductName': 'Palle Ibsen', 'ProductID': 'Rogede sild', 'CustomerID': 'RATTC', 'CustomerName': 'Paula Wilson'},
            {'OrderID': ++primaryKey, 'ProductName': 'Francisco Chang', 'ProductID': 'Mascarpone Fabioli', 'CustomerID': 'ROMEY', 'CustomerName': 'Jose Pavarotti'}
        ]
    let aData = immutableGrid.dataSource.concat(addedRecords);
    normalGrid.setProperties({ dataSource: aData });
    immutableGrid.setProperties({ dataSource: aData });
});

document.getElementById('reverse').addEventListener('click', function(e) {
    let aData = immutableGrid.dataSource.reverse();
    normalGrid.setProperties({ dataSource: aData });
    immutableGrid.setProperties({ dataSource: aData });
});

document.getElementById('paging').addEventListener('click', function(e) {
    let totalPage = immutableGrid.dataSource.length / immutableGrid.pageSettings.pageSize;
    let page = Math.floor(Math.random() * totalPage) + 1;
    normalGrid.setProperties({ pageSettings: { currentPage: page } });
    immutableGrid.setProperties({ pageSettings: { currentPage: page } });
});

let normalGrid: Grid = new Grid({
    dataSource: data,
    allowPaging: true,
    pageSettings: { pageSize: 50 },
    beforeDataBound: () => {
        normalStart = new Date().getTime();
    },
    dataBound: ()=> {
        let val = init ? '' : new Date().getTime() - normalStart;
        document.getElementById('normalDelete').innerHTML = 'Normal rendering Time: ' + "<b>" + val + "</b>" + '<b>ms</b>';
        normalStart = 0; init = false;
    },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', isPrimaryKey: true, textAlign: 'Right', width: 120 },
        { field: 'ProductName', headerText: 'Product Name', width: 160 },
        { field: 'ProductID', headerText: 'Product ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120 },
        { field: 'CustomerName', headerText: 'Customer Name', width: 160 }
    ],
    height: 240
});
normalGrid.appendTo('#normal');

```

{% endtab %}

## Limitations

The following features are not supported in the immutable mode:

* Frozen rows and columns
* Row Template
* Detail Template
* Hierarchy Grid
* Column reorder
* Virtualization
* Infinite scroll
* Grouping
