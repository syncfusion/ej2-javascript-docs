---
title: "Columns"
component: "TreeGrid"
description: "Documentation on column reordering, resizing, header templates (custom header content), and column templates (custom cell content) in the Essential JS 2 TreeGrid control."
---

# Columns

The column definitions are used as the [`dataSource`](../api/treegrid#dataSource) schema in the TreeGrid. This plays a vital role in rendering column values in the required format.
The treegrid operations such as sorting, filtering and searching etc. are performed based on column definitions. The [`field`](../api/treegrid/column/#field) property of the [`columns`](../api/treegrid#column)
is necessary to map the data source values in TreeGrid columns.

> 1. If the column [`field`](../api/treegrid/column/#field) is not specified in the dataSource, the column values will be empty.
> 2. If the [`field`](../api/treegrid/column/#field) name contains “dot” operator, it is considered as complex binding.

[`treeColumnIndex`](../api/treegrid#treecolumnindex) property denotes the column that is used to expand and collapse child rows.

## Header Template

You can customize the header element by using the [`headerTemplate`](../api/treegrid/column/#headerTemplate) property.

{% tab template="treegrid/header-template", es5Template="headertemplate" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { headerData } from './datasource.ts';
let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: headerData,
    childMapping: 'subtasks',
    height: 315,
    columns: [  
        { field: 'taskName', headerTemplate: '#projectName', width: 220 },
        { field: 'startDate', headerTemplate: '#dateTemplate', format: 'yMd', textAlign: 'Right' },
        { field: 'duration', headerTemplate: '#durationTemplate', textAlign: 'Right' },
        { field: 'progress', headerTemplate: '#progressTemplate', textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Header text

By default, column header title is displayed from column [`field`](../api/treegrid/column/#field) value. To override the default header title, you have to define the [`headerText`](../api/treegrid/column/#headertext) value.

{% tab template="treegrid/columns", es5Template="headerText" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 315,
    treeColumnIndex: 1,
    columns: [
                { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
                {
                    field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
                },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

> * If both the [`field`](../api/treegrid/column/#field) and [`headerText`](../api/treegrid/column/#headertext) are not defined in the column, the column renders with “empty” header text.

## Format

To format cell values based on specific culture, use the [`columns.format`](../api/treegrid/column/#format) property. The TreeGrid uses [Internalization](../common/internationalization/) library to format [`number`](../common/internationalization/#number-formatting) and [`date`](../common/internationalization/#manipulating-datetime)
values.

{% tab template="treegrid/columns", es5Template="formatting" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { formatData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: formatData,
    childMapping: 'subtasks',
    height: 315,
    treeColumnIndex: 1,
    columns: [
                { field: 'orderID', headerText: 'Order ID', textAlign: 'Right', width: 90 },
                { field: 'orderName', headerText: 'Order Name', textAlign: 'Left', width: 180 },
                { field: 'price', headerText: 'Price', textAlign: 'Right', width: 90, format: 'c2', type: 'number' },
            ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

> By default, the [`number`](../common/internationalization/#number-formatting) and [`date`](../common/internationalization/#manipulating-datetime) values are formatted in `en-US` locale.

### Number formatting

The number or integer values can be formatted using the below format strings.

Format |Description |Remarks
-----|-----
N | Denotes numeric type. | The numeric format is followed by integer value as N2, N3. etc which denotes the number of precision to be allowed.
C | Denotes currency type. | The currency format is followed by integer value as C2, C3. etc which denotes the number of precision to be allowed.
P | Denotes percentage type | The percentage format expects the input value to be in the range of 0 to 100. For example the cell value `0.2` is formatted as `20%`. The percentage format is followed by integer value as P2, P3. etc which denotes the number of precision to be allowed.

Please refer to the link to know more about [`Number formatting`](../common/internationalization/#number-formatting).

### Date formatting

You can format date values either using built-in date format string or custom format string.

For built-in date format you can specify [`columns.format`](../api/treegrid/column/#format) property as string   (Example: `yMd`). Please refer to the link to know more about [`Date formatting`](../common/internationalization/#manipulating-datetime).

You can also use custom format string to format the date values. Some of the custom formats and the formatted date values are given in the below table.

Format | Formatted value
-----|-----
{ type:'date', format:'dd/MM/yyyy' } | 04/07/1996
{ type:'date', format:'dd.MM.yyyy' } | 04.07.1996
{ type:'date', skeleton:'short' } | 7/4/96
{ type: 'dateTime', format: 'dd/MM/yyyy hh:mm a' } | 04/07/1996 12:00 AM
{ type: 'dateTime', format: 'MM/dd/yyyy hh:mm:ss a' } | 07/04/1996 12:00:00 AM

{% tab template="treegrid/columns", es5Template="dateformatting" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { formatData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: formatData,
    childMapping: 'subtasks',
    height: 315,
    treeColumnIndex: 1,
    columns: [
                { field: 'orderID', headerText: 'Order ID', textAlign: 'Right', width: 90 },
                { field: 'orderName', headerText: 'Order Name', textAlign: 'Left', width: 220 },
                {
                    field: 'orderDate', headerText: 'Order Date', textAlign: 'Right', width: 160,
                    format: { format: 'dd/MM/yyyy', type: 'date' }
                },
                { field: 'price', headerText: 'Price', textAlign: 'Right', width: 90, format: 'c2', type: 'number' },
            ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## AutoFit specific columns

The [`autoFitColumns`](../api/treegrid/#autofitcolumns) method resizes the column to fit the widest cell's content without wrapping. You can autofit a specific column at initial rendering by invoking the [`autoFitColumns`](../api/treegrid/#autofitcolumns) method in [`dataBound`](../api/treegrid/#databound) event.

{% tab template="treegrid/columns", es5Template="autofit" %}

```typescript
import { TreeGrid, Resize } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Resize);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowResizing: true,
    dataBound: () => treeGridObj.autoFitColumns(['taskName']),
    height: 315,
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', textAlign: 'Right', width: 90 },
        { field: 'taskName', headerText: 'Task Name', width: 60 },
        {
            field: 'startDate', headerText: 'Start Date', format: 'yMd', width: 120, textAlign:'Right'
        },
        { field: 'duration', headerText: 'Duration', width: 120, textAlign: 'Right' },
        { field: 'progress', headerText: 'Progress', width: 120, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

> You can autofit all the columns by invoking the [`autoFitColumns`](../api/treegrid/column/#autofitcolumns) method without column names.

## Reorder

Reordering can be done by drag and drop of a particular column header from one index to another index within the treegrid. To enable reordering, set the [`allowReordering`](../api/treegrid/#allowreordering) to true.

To use reordering, inject the [`Reorder`](../api/treegrid/#reordermodule) module in the treegrid.

{% tab template="treegrid/columns" , es5Template="reorder" %}

```typescript
import { TreeGrid, Reorder } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Reorder);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowReordering: true,
    height: 315,
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', textAlign: 'Right', width: 90 },
        { field: 'taskName', headerText: 'Task Name', width: 180 },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
        { field: 'progress', headerText: 'Progress', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

> You can disable reordering a particular column by setting the [`columns.allowReordering`](../api/treegrid/column/#reordermodule) to false.

### Reorder Multiple Columns

Multiple columns can be reordered at a time by using the [`reorderColumns`](../api/treegrid/column/#reordercolumns) method.

{% tab template="treegrid/reorder-columns" , es5Template="reorderbyColumn" %}

```typescript
import { TreeGrid, Reorder } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';
import { Button } from '@syncfusion/ej2-buttons';

TreeGrid.Inject(Reorder);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowReordering: true,
    height: 285,
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', textAlign: 'Right', width: 90 },
        { field: 'taskName', headerText: 'Task Name', width: 180 },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
        { field: 'progress', headerText: 'Progress', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

let reorderMultipleColsBtn: Button = new Button();
reorderMultipleColsBtn.appendTo('#reorderMultipleCols');

document.getElementById('reorderMultipleCols').addEventListener('click', () => {
    treeGridObj.reorderColumns(['taskID','duration'],'progress');
});

```

{% endtab %}

## Lock Columns

You can lock columns by using [`column.lockColumn`](../api/treegrid/column/#lockcolumn) property. The locked columns will be moved to the first position. Also you can’t reorder its position.

In the below example, duration column is locked and its reordering functionality is disabled.

{% tab template="treegrid/columns", sourceFiles="index.ts,index.css" es5Template="lockColumn" %}

```typescript
import { TreeGrid, Reorder } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Reorder);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowReordering: true,
    allowSelection: false,
    height: 315,
    treeColumnIndex: 1,
    columns: [
                { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
                {
                    field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
                },
                { field: 'duration', headerText: 'Duration', width: 80, lockColumn: true, customAttributes: {class: 'customcss'}, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Column resizing

Column width can be resized by clicking and dragging the right edge of the column header. While dragging, the width of the respective column will be resized immediately. Each column can be auto resized by double-clicking the right edge of the column header to fit the width of that column based on the widest cell content. To enable column resize, set the [`allowResizing`](../api/treegrid/#allowresizing) property to true.

To use the column resize, inject `Resize` module in the treegrid.

{% tab template="treegrid/resize", es5Template="resizing" %}

```typescript
import { TreeGrid, Resize } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Resize);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowResizing: true,
    height: 315,
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', textAlign: 'Right', width: 90 },
        { field: 'taskName', headerText: 'Task Name', width: 180 },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
        { field: 'progress', headerText: 'Progress', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

> * You can disable resizing for a particular column by setting the [`columns.allowResizing`](../api/treegrid/column/#allowresizing) to false.
> * In RTL mode, you can click and drag the left edge of the header cell to resize the column.

### Min and max width

Column resize can be restricted between minimum and maximum width by defining the [`columns->minWidth`](../api/treegrid/column/#minwidth) and [`columns->maxWidth`](../api/treegrid/column/#maxwidth).

In the following sample, minimum and maximum width are defined for `Duration`, and `Task Name` columns.

{% tab template="treegrid/resize", es5Template="minmax" %}

```typescript
import { TreeGrid, Resize } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Resize);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowResizing: true,
    height: 315,
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', textAlign: 'Right', width: 90 },
        { field: 'taskName', headerText: 'Task Name', minWidth: 170, maxWidth: 250, width: 180 },
        { field: 'duration', headerText: 'Duration', width: 80, minWidth: 50, maxWidth: 150,  textAlign: 'Right' },
        { field: 'progress', headerText: 'Progress', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

### Resize Stacked Column

Stacked columns can be resized by clicking and dragging the right edge of the stacked column header. While dragging, the width of the respective child columns will be resized at the same time. You can disable resize for particular stacked column by setting `allowResizing` as `false` to its columns.

{% tab template="treegrid/resize", es5Template="stackedresize" %}

```typescript
import { TreeGrid, Resize } from '@syncfusion/ej2-treegrid';
import { stackedData } from './datasource.ts';

TreeGrid.Inject(Resize);

let treeGridObj: TreeGrid = new TreeGrid(
    {
        dataSource: stackedData,
        childMapping: 'subtasks',
        allowResizing: true,
        treeColumnIndex: 1,
        height: 260
        columns: [
            {
                headerText: 'Order Details', textAlign: 'Center', columns: [
                    { field: 'orderID', headerText: 'Order ID', textAlign: 'Right', width: 90 },
                    { field: 'orderName', headerText: 'Order Name', textAlign: 'Left', width: 170 },
                ]
            },
            {
                headerText: 'Shipment Details', textAlign: 'Center', columns: [
                    { field: 'shipMentCategory', headerText: 'Shipment Category', textAlign: 'Left', width: 90 },
                    { field: 'shippedDate', headerText: 'Shipped Date', textAlign: 'Right', width: 90, format: 'yMd' }
                ]
            }
        ]
    });
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

### Touch interaction

When the right edge of the header cell is tapped, a floating handler will be visible over the right border of the column. To resize the column, tap and drag the floating handler as needed.

The following screenshot represents the column resizing in touch device.

<!-- markdownlint-disable MD033 -->
<img src="../images/column-resizing.png" alt="Touch interaction image" style="width:320px;height: 620px">
<!-- markdownlint-enable MD033 -->

## Column template

The column [`template`](../api/treegrid/column/#template) has options to display custom element instead of a field value in the column.

{% tab template="treegrid/column-template", sourceFiles="index.ts,index.html", es5Template="template" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { textdata,getSparkData } from './datasource.ts';
import { Sparkline } from '@syncfusion/ej2-charts';
import { RowDataBoundEventArgs, getObject } from '@syncfusion/ej2-grids';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: textdata,
    childMapping: 'Children',
    treeColumnIndex: 0,
    rowDataBound: (args: RowDataBoundEventArgs) : void => {
        let data: string = getObject('EmployeeID', args.data);
        let spkwl: HTMLElement = args.row.querySelector('#spkwl' + data);
        let winloss: Sparkline = new Sparkline({
            height: '50px',
            width: '150px',
            type: 'WinLoss',
            valueType: 'Numeric',
            fill: '#3C78EF',
            tiePointColor: 'darkgray',
            negativePointColor: '#f7a816',
            dataSource: getSparkData('column', +data)
        });
        winloss.appendTo(spkwl);
    },
    rowHeight: 83,
    columns: [
        { field: 'EmpID', headerText: 'Employee ID', width: 95 },
        { field: 'Name', headerText: 'Name', width: 110 },
        { field: 'DOB', headerText: 'DOB', width: 90, textAlign: 'Right', format: 'yMd' },
        {
            headerText: 'Year GR', textAlign: 'Center',
            template: '#template', width: 120
        }
    ]
    height: 260
});
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}
> TreeGrid actions such as editing, filtering and sorting etc. will depend upon the column [`field`](../api/treegrid/column/#field). If the [`field`](../api/treegrid/column/#field) is not specified in the
template column, the treegrid actions cannot be performed.

### Using condition template

You can render the template elements based on condition.

In the following code, checkbox is rendered based on `Approved` field value.

```html
  <script id="template" type="text/x-template">
            <div class="template_checkbox">
                ${if(approved)}
                <input type="checkbox" checked> ${else}
                <input type="checkbox"> ${/if}
            </div>
        </script>
```

{% tab template="treegrid/condition-inside-template", sourceFiles="index.ts,index.html", es5Template="condition-template" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowResizing: true,
    height: 315,
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', textAlign: 'Right', width: 90 },
        { field: 'taskName', headerText: 'Task Name', width: 180 },
        {
            headerText: 'Approved', textAlign: 'Center',
            template: '#template', width: 120
        },
        { field: 'progress', headerText: 'Progress', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Column type

Column type can be specified using the [`columns.type`](../api/treegrid/column/#type) property. It specifies the type of data the column binds.

If the [`format`](../api/treegrid/column/#format)  is defined for a column, the column uses [`type`](../api/treegrid/column/#type) to select the appropriate format option ([number](../common/internationalization/#number-formatting)
 or [date](../common/internationalization/#manipulating-datetime)).

TreeGrid column supports the following types:

* string
* number
* boolean
* date
* datetime

> If the [`type`](../api/treegrid/column/#type) is not defined, it will be determined from the first record of the [`dataSource`](../api/treegrid/column/#datasource).

## Column chooser

The column chooser has options to show or hide columns dynamically. It can be enabled by defining the
[`showColumnChooser`](../api/treegrid/#showcolumnchooser) as true.

To use the column chooser, inject the **Column Chooser** module in the treegrid.

{% tab template="treegrid/columns", es5Template="columnchooser" %}

```typescript
import { TreeGrid, Selection, Toolbar, ColumnChooser } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Selection, Toolbar, ColumnChooser);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    showColumnChooser: true,
    treeColumnIndex: 1,
    toolbar: ['ColumnChooser'],
    columns: [
        { field: 'taskID', headerText: 'Task ID', textAlign: 'Right', width: 90 },
        { field: 'taskName', headerText: 'Task Name', width: 240, showInColumnChooser: false },
        { field: 'startDate', headerText: 'Start Date', width: 110, format: 'yMd' },
        { field: 'endDate', headerText: 'End Date', width: 110, textAlign: 'Right', type: 'date', format: 'yMd' },
        { field: 'duration', headerText: 'Duration', width: 100, textAlign: 'Right' },
        { field: 'progress', headerText: 'Progress', width: 100, textAlign: 'Right' },
        { field: 'priority', headerText: 'Priority', width: 90 }
    ]
    height: 315
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

> You can hide the column names in column chooser by defining the [`columns.showInColumnChooser`](../api/treegrid/column/#showincolumnchooser) as false.

### Open column chooser by external button

The Column chooser can be displayed on a page through external button by invoking
the [`openColumnChooser`](../api/treegrid/#opencolumnchooser) method with **X** and **Y** axis positions.

{% tab template="treegrid/columnchooser-method", sourceFiles="index.ts,index.html", es5Template="chooser"%}

```typescript
import { TreeGrid, Selection, ColumnChooser } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';
import { Button } from '@syncfusion/ej2-buttons';

TreeGrid.Inject(Selection, ColumnChooser);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    treeColumnIndex: 1,
    showColumnChooser: true,
    columns: [
        { field: 'taskID', headerText: 'Task ID', textAlign: 'Right', width: 90 },
        { field: 'taskName', headerText: 'Task Name', width: 240, showInColumnChooser: false },
        { field: 'startDate', headerText: 'Start Date', width: 110, format: 'yMd' },
        { field: 'endDate', headerText: 'End Date', width: 110, textAlign: 'Right', type: 'date', format: 'yMd' },
        { field: 'duration', headerText: 'Duration', width: 100, textAlign: 'Right' },
        { field: 'progress', headerText: 'Progress', width: 100, textAlign: 'Right' },
        { field: 'priority', headerText: 'Priority', width: 90 }
    ]
    height: 315
});

treeGridObj.appendTo('#TreeGrid');

let show: Button = new Button({ cssClass: 'e-flat' }, '#show');

document.getElementById('show').onclick = () => {
    treeGridObj.columnChooserModule.openColumnChooser(200, 50); // give X and Y axis
};

```

{% endtab %}

## Column menu

The column menu has options to integrate features like sorting, filtering, and autofit. It will show a menu with the integrated feature when users click on multiple icon of the column. To enable column menu, you need to define the [`showColumnMenu`](../api/treegrid/#showcolumnmenu) property as true.

To use the column menu, inject the `ColumnMenu` module in the treegrid.

The default items are displayed in following table.

| Item | Description |
|-----|-----|
| `SortAscending` | Sort the current column in ascending order. |
| `SortDescending` | Sort the current column in descending order. |
| `AutoFit` | Auto fit the current column. |
| `AutoFitAll` | Auto fit all columns. |
| `Filter` | Show the filter option as given in `filterSettings.type` |

{% tab template="treegrid/columns", es5Template="columnmenu" %}

```typescript
import {TreeGrid, Sort, Page, Filter, Resize, ColumnMenu} from '@syncfusion/ej2-treegrid';
import { sampleData  } from './datasource.ts';

TreeGrid.Inject(Page, Filter, Sort, Resize, ColumnMenu );

let treegrid: TreeGrid = new TreeGrid(
    {
        dataSource: sampleData,
        childMapping: 'subtasks',
        height: 315,
        allowFiltering: true,
        allowResizing: true,
        filterSettings: { type: 'Menu' },
        allowSorting: true,
        showColumnMenu: true,
        treeColumnIndex: 1,
        columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180 },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
        ]
    });
treegrid.appendTo('#TreeGrid');


```

{% endtab %}

> * You can disable column menu for a particular column by defining the [`columns.showColumnMenu`](../api/treegrid/column/#showcolumnmenu) as false.

## Checkbox Column

To render checkboxes in existing column, you need to set [`columns.showCheckbox`] property as `true`.

It is also possible to select the rows hierarchically using checkboxes in TreeGrid by enabling [`autoCheckHierarchy`] property. When we check on any parent record checkbox then the child record checkboxes will get checked.

{% tab template="treegrid/columns", es5Template="checkboxcolumn" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { data, sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 315,
    autoCheckHierachy: true,
    treeColumnIndex: 1,
    columns: [
                { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', showCheckbox: true, width: 180 },
                { field: 'approved', headerText: 'Approved', width: 90 },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Responsive columns

You can toggle column visibility based on media queries which are defined
at the [`hideAtMedia`](../api/treegrid/column/#hideatmedia).
The [`hideAtMedia`](../api/treegrid/column/#hideatmedia) accepts valid
[Media Queries]( http://cssmediaqueries.com/what-are-css-media-queries.html ).

{% tab template="treegrid/columns", sourceFiles="index.ts,index.html", es5Template="responsive" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 315,
    treeColumnIndex: 1,
    columns: [
                {
                    field: 'taskID', headerText: 'Task ID', hideAtMedia: '(min-width: 700px)', width:90, textAlign: 'Right'
                },// column hides when browser screen width lessthan 700px;
                { field: 'taskName', headerText: 'Task Name', width: 180 },
                {
                    field: 'startDate', headerText: 'Start Date', hideAtMedia: '(max-width: 500px)',width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
                }, // column shows when browser screen width lessthan or equalto 500px;
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Controlling TreeGrid actions

You can enable or disable treegrid action for a particular column by setting the [`allowFiltering`](../api/treegrid/column/#allowfiltering), and [`allowSorting`](../api/treegrid/column/#allowsorting) properties.

{% tab template="treegrid/columns", es5Template="gridaction" %}

```typescript
import { TreeGrid, Filter, Sort } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Filter, Sort);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 270,
    treeColumnIndex: 1,
    allowSorting: true,
    allowFiltering: true,
    columns: [
                {
                    field: 'taskID', headerText: 'Task ID', allowSorting: false, width: 90,textAlign: 'Right'
                },
                { field: 'taskName', headerText: 'Task Name', width: 180 },
                {
                    field: 'startDate', headerText: 'Start Date', allowFiltering: false, width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
                },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');


```

{% endtab %}

## Show/hide columns by external button

You can show or hide treegrid columns dynamically using external buttons by invoking the [`showColumns`](../api/treegrid/#showcolumns) or [`hideColumns`](../api/treegrid/#hidecolumns) method.

{% tab template="treegrid/show-hide-columns", sourceFiles="index.ts,index.html", es5Template="showhide"%}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';
import { Button } from '@syncfusion/ej2-buttons';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 270,
    treeColumnIndex: 1,
    columns: [
                { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 180 },
                {
                    field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
                },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

let show: Button = new Button({ cssClass: 'e-flat' }, '#show');
let hide: Button = new Button({ cssClass: 'e-flat' }, '#hide');

document.getElementById('show').onclick = () => {
    treeGridObj.showColumns(['Task ID', 'Duration']); //show by HeaderText
};

document.getElementById('hide').onclick = () => {
    treeGridObj.hideColumns(['Task ID', 'Duration']); //hide by HeaderText
};

```

{% endtab %}

## Complex data binding

You can achieve complex data binding in the treegrid by using the dot(.) operator in the [`column.field`](../api/treegrid/column/#field).

{% tab template="treegrid/columns", sourceFiles="index.ts,datasource.ts", es5Template="complexbinding"  %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { complexData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: complexData,
    childMapping: 'subtasks',
    height: 315,
    treeColumnIndex: 1,
    columns: [
                { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 180 },
                { field: 'assignee.firstName', headerText: 'Assignee', width: 90},
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## ValueAccessor

The [`valueAccessor`](../api/treegrid/column/#valueaccessor) is used to access/manipulate the value of display data. You can achieve custom value formatting by using the [`valueAccessor`](../api/treegrid/column/#valueaccessor).

{% tab template="treegrid/columns", sourceFiles="index.ts,index.html,datasource.ts", es5Template="value" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { formatData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: formatData,
    childMapping: 'subtasks',
    height: 315,
    treeColumnIndex: 1,
    columns: [
            { field: 'orderID', headerText: 'Order ID', textAlign: 'Right', width: 100 },
            {
                field: 'orderName', headerText: 'Order Name', textAlign: 'Left',  valueAccessor:orderFormatter, width: 215
            },
            {
                field: 'orderDate', headerText: 'Order Date', textAlign: 'Right', width: 110,
                format: { format: 'dd/MM/yyyy', type: 'date' }
            },
            {
                field: 'price', headerText: 'Price', textAlign: 'Right', width: 100, valueAccessor:currencyFormatter, type: 'number'
            },
    ],
    height: 315
});
treeGridObj.appendTo('#TreeGrid');

function currencyFormatter(field: string, data: Object, column: Object): string {
    return '€' + data['price'];
}

function orderFormatter(field: string, data: Object, column: Object): string {
    return data[field] + '-' + data['Category'];
}

```

{% endtab %}

### Display array type columns

You can bind an array of objects in a column by using the [`valueAccessor`](../api/treegrid/column/#valueaccessor) property.
In this example, the name field has an array of two objects, FirstName and LastName. These two objects are joined and bound to a column using the
[`valueAccessor`](../api/treegrid/column/#valueaccessor).

{% tab template="treegrid/columns", sourceFiles="index.ts,index.html,datasource.ts", es5Template="valuearray"%}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { stringData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: stringData,
    childMapping: 'subtasks',
    height: 315,
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', textAlign: 'Right', width: 110 },
            { field: 'taskName', headerText: 'Task Name', width: 180 },
            {
                field: 'name', headerText: 'Assignee', textAlign: 'Left', valueAccessor:orderFormatter, width: 150
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ],
    height: 315
});
treeGridObj.appendTo('#TreeGrid');


function orderFormatter(field: string, data: Object, column: Object): string {
    return data[field].map(function (s: {lastName: string, firstName: string}): string {
        return s.lastName || s.firstName }).join(' ');
}

```

{% endtab %}

### Expression column

You can achieve the expression column by using the [`valueAccessor`](../api/treegrid/column/#valueaccessor) property.

{% tab template="treegrid/columns", es5Template="expression" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { formatData } from './datasource.ts';

let treegrid: TreeGrid = new TreeGrid(
    {
        dataSource: formatData,
        height: 315,
        childMapping: 'subtasks',
        treeColumnIndex: 1,
        columns: [
            { field: 'orderID', headerText: 'Order ID', textAlign: 'Right', width: 110 },
            { field: 'orderName', headerText: 'Order Name', textAlign: 'Left', width: 210 },
            { field: 'units', headerText: 'Units', textAlign: 'Right', width: 120 },
            { field: 'unitPrice', headerText: 'Unit Price', textAlign: 'Right', width: 120, format: 'c2', type: 'number' },
            { field: 'price', headerText: 'Total Price', valueAccessor: totalPrice, textAlign: 'Right', width: 120, format: 'c2', type: 'number' },
        ]
    });
treegrid.appendTo('#TreeGrid');

function totalPrice(field: string, data: { units: number, Fat: number, unitprice: number }, column: Object): number {
    return data.units * data.unitPrice;
};

```

{% endtab %}

## How to render boolean values as checkbox

To render boolean values as checkbox in columns, you need to set [`displayAsCheckBox`](../api/treegrid/column/#displayascheckbox) property as `true`.

{% tab template="treegrid/columns", es5Template="displayascheckbox" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { data, sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 315,
    treeColumnIndex: 1,
    columns: [
                { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 180 },
                { field: 'approved', headerText: 'Approved', displayAsCheckBox: true, width: 90 },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}
