---
title: "Aggregates"
component: "TreeGrid"
description: "Learn how to aggregate rows, apply custom aggregates, and format the aggregate values in the Essential JS 2 TreeGrid control."
---

# Aggregates

Aggregate values are displayed in the TreeGrid footer and in parent row footer for child row aggregate values. It can be configured through `aggregates` property.
 [`field`](../api/treegrid/aggregateColumnModel/#field) and [`type`](../api/treegrid/aggregateColumnModel/#type)
 are the minimum properties required to represent an aggregate column.

To use the aggregate feature, you have to inject the `Aggregate` module.

By default, the aggregate value can be displayed in the treegrid footer, and footer of child rows. To show the aggregate value in one of the cells, use the [`footerTemplate`](../api/treegrid/aggregateColumnModel/#footertemplate).

## Built-in aggregate types

The aggregate type should be specified in the [`type`](../api/treegrid/aggregateColumnModel/#type) property to configure an aggregate column.

The built-in aggregates are,

* Sum
* Average
* Min
* Max
* Count
* Truecount
* Falsecount

> * Multiple aggregates can be used for an aggregate column by setting the [`type`](../api/treegrid/aggregateColumnModel/#type) property with an array of aggregate types.
> * Multiple types for a column is supported only when one of the aggregate templates is used.

## Footer aggregate

Footer aggregate value is calculated for all the rows, and it is displayed in the footer cells. Use the [`footerTemplate`](../api/treegrid/aggregateColumnModel/#footertemplate) property to render the aggregate value in footer cells.

{% tab template="treegrid/aggregates", es5Template="footer" %}

```typescript
import { TreeGrid, Aggregate } from '@syncfusion/ej2-treegrid';
import { summaryRowData } from './datasource.ts';

TreeGrid.Inject(Aggregate);

let treeGridObj: TreeGrid = new TreeGrid(
    {
        dataSource: summaryRowData,
        childMapping: 'children',
        treeColumnIndex: 0,
        height: 260,
        columns: [
            { field: 'FreightID', headerText: 'Freight ID', width: 130 },
            { field: 'FreightName', width: 195, headerText: 'Freight Name' },
            { field: 'UnitWeight', headerText: 'Weight Per Unit', type: 'number', width: 130, textAlign: 'Right' },
            { field: 'TotalUnits', headerText: 'Total Units', type: 'number', width: 125, textAlign: 'Right' }
        ],
        aggregates: [{
            showChildSummary: false,
            columns: [
                {
                    type: 'Max',
                    field: 'UnitWeight',
                    columnName: 'UnitWeight',
                    footerTemplate: 'Maximum: ${Max}'
                },
                {
                type: 'Min',
                field: 'TotalUnits',
                columnName: 'TotalUnits',
                footerTemplate: 'Minimum: ${Min}'
            }]
        }]
    });
treeGridObj.appendTo('#TreeGrid');
```

{% endtab %}

> The aggregate values must be accessed inside the template using their corresponding [`type`](../api/treegrid/aggregateColumnModel/#type) name.

## Child aggregate

Aggregate value is calculated for child rows, and it is displayed in the parent row footer. Use the [`childSummary`](../api/treegrid/aggregateRowModel/#showchildsummary) property to render the child rows aggregate value.

{% tab template="treegrid/aggregates", es5Template="childfooter" %}

```typescript
import { TreeGrid, Aggregate } from '@syncfusion/ej2-treegrid';
import { summaryRowData } from './datasource.ts';

TreeGrid.Inject(Aggregate);

let treeGridObj: TreeGrid = new TreeGrid(
    {
        dataSource: summaryRowData,
        childMapping: 'children',
        treeColumnIndex: 0,
        height: 260,
        columns: [
            { field: 'FreightID', headerText: 'Freight ID', width: 130 },
            { field: 'FreightName', width: 195, headerText: 'Freight Name' },
            { field: 'UnitWeight', headerText: 'Weight Per Unit', type: 'number', width: 130, textAlign: 'Right' },
            { field: 'TotalUnits', headerText: 'Total Units', type: 'number', width: 125, textAlign: 'Right' }
        ],
        aggregates: [{
            showChildSummary: true,
            columns: [
                {
                    type: 'Max',
                    field: 'UnitWeight',
                    columnName: 'UnitWeight',
                    footerTemplate: 'Maximum: ${Max}'
                },
                {
                type: 'Min',
                field: 'TotalUnits',
                columnName: 'TotalUnits',
                footerTemplate: 'Minimum: ${Min}'
            }]
        }]
    });
treeGridObj.appendTo('#TreeGrid');
```

{% endtab %}

## How to format aggregate value

You can format the aggregate value result by using the [`format`](../api/treegrid/aggregateColumnModel/#type) property.

{% tab template="treegrid/aggregates",es5Template="format" %}

```typescript
import { TreeGrid, Aggregate } from '@syncfusion/ej2-treegrid';
import { summaryData } from './datasource.ts';

TreeGrid.Inject(Aggregate);

let treeGridObj: TreeGrid = new TreeGrid(
    {
        dataSource: summaryData,
        childMapping: 'subtasks',
        treeColumnIndex: 0,
        height: 260,
        columns: [
            { field: 'category', headerText: 'Category', width: 160 },
            { field: 'units', headerText: 'Total Units', width: 130, type: 'number', textAlign: 'Right' },
            { field: 'unitPrice', headerText: 'Unit Price($)', width: 110, type: 'number', format: 'C2', textAlign: 'Right' },
            { field: 'price', headerText: 'Price($)', width: 160, textAlign: 'Right', type: 'number', format: 'C2' },
        ],
        aggregates: [{
            columns: [
                {
                    type: 'Sum',
                    field: 'price',
                    columnName: 'price',
                    format: 'C2',
                    footerTemplate: 'Total: ${Sum}'
                }]
        }]
    });
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Custom aggregate

To calculate the aggregate value with your own aggregate functions, use the custom aggregate option. To use custom aggregation, specify the [`type`](../api/treegrid/aggregateColumnModel/#type) as `Custom`, and provide the custom aggregate function in the [`customAggregate`](../api/treegrid/aggregateColumnModel/#customaggregate) property.

{% tab template="treegrid/aggregates", es5Template="custom" %}

```typescript
import { TreeGrid, Aggregate } from '@syncfusion/ej2-treegrid';
import { summaryData } from './datasource.ts';
import { getObject, CustomSummaryType } from '@syncfusion/ej2-grids';

let customAggregateFn: CustomSummaryType = (data: Object): number => {
    let sampleData: Object[] = getObject('result', data);
    let countLength: number; countLength = 0;
    sampleData.filter((item: Object) => {
        let data: string = getObject('category', item);
        if (data === 'Frozen seafood') {
            countLength++;
        }
    });
    return countLength;
};

TreeGrid.Inject(Aggregate);

let treeGridObj: TreeGrid = new TreeGrid(
    {
        dataSource: summaryData,
        childMapping: 'subtasks',
        width: 'auto',
        height: 245,
        treeColumnIndex: 1,
        columns: [
            { field: 'category', headerText: 'Category', width: 200 },
            { field: 'units', headerText: 'Total Units', width: 130, type: 'number', textAlign: 'Right' },
            { field: 'unitPrice', headerText: 'Unit Price($)', width: 110, type: 'number', format: 'C2', textAlign: 'Right' },
            { field: 'price', headerText: 'Price($)', width: 110, textAlign: 'Right', type: 'number', format: 'C' },
        ],
        aggregates: [{
            showChildSummary: false,
            columns: [{
                type: 'Custom',
                customAggregate: customAggregateFn,
                columnName: 'category',
                footerTemplate: 'Count of Frozen seafood : ${Custom}'
            }]
        }]
    });
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

> To access the custom aggregate value inside the template, use the key as `Custom`.