---
title: "Worksheet"
component: "Spreadsheet"
description: "Learn the various operations that we can perform in worksheet of the Essential JS 2 Spreadsheet."
---

# Worksheet

Worksheet is a collection of cells organized in the form of rows and columns that allows you to store, format, and manipulate the data.

## Add sheet

You can dynamically add or insert a sheet by one of the following ways,

* Click the `Add Sheet` button in the sheet tab. This will add a new empty sheet next to current active sheet.
* Right-click on the sheet tab, and then select `Insert` option from the context menu to insert a new empty sheet before the current active sheet.
* Using [`insertSheet`](../api/spreadsheet/#insertsheet) method, you can insert one or more sheets at your desired index.

The following code example shows the insert sheet operation in spreadsheet.

{% tab template="spreadsheet/insert/sheet", sourceFiles="app.ts,index.html,datasource.ts", es5Template="es5-insert-sheet", iframeHeight="450px", isDefaultActive=true %}

```typescript
import { Spreadsheet, SheetModel } from '@syncfusion/ej2-spreadsheet';
import { data } from './datasource.ts';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let sheets: SheetModel[] = [{
    name: 'Price Details',
    ranges: [{ dataSource: data }],
    columns: [{ width: 150 }, { width: 110 }, { width: 110 }, { width: 85 }, { width: 85 }, { width: 85 }, { width: 85 },
        { width: 85 }]
}];

let spreadsheet: Spreadsheet = new Spreadsheet({
    sheets: sheets,
    created: (): void => {
        // Applies style formatting to the active sheet before inserting a new sheet
        spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center' }, 'A1:H1');
        spreadsheet.cellFormat({ textAlign: 'center' }, 'D2:H11');
        // inserting a new sheet with data at 1st index
        // You can also insert empty sheets by specifying the start and end sheet index instead of sheet model
        spreadsheet.insertSheet([{
            index: 1,
            name: 'Inserted Sheet',
            ranges: [{ dataSource: data }],
            columns: [{ width: 150 }, { width: 110 }, { width: 110 }, { width: 85 }, { width: 85 }, { width: 85 }, { width: 85 },
                { width: 85 }]
        }]);
        // Applies style formatting for the inserted sheet
        spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center' }, 'Inserted Sheet!A1:H1');
        spreadsheet.cellFormat({ textAlign: 'center' }, 'Inserted Sheet!D2:H11');
    },
    // Removed the unwanted support for this samples
    showRibbon: false, showFormulaBar: false
});

spreadsheet.appendTo('#spreadsheet');
```

{% endtab %}

## Delete sheet

The Spreadsheet has support for removing an existing worksheet. You can dynamically delete the existing sheet by the following way,

* Right-click on the sheet tab, and then select `Delete` option from context menu.

## Rename sheet

You can dynamically rename an existing worksheet in the following way,

* Right-click on the sheet tab, and then select `Rename` option from the context menu.

## Headers

By default, the row and column headers are visible in worksheets. You can dynamically show or hide worksheet headers by using one of the following ways,

* Switch to `View` tab, and then select `Hide Headers` option to hide both the row and column headers.
* Set `showHeaders` property in `sheets` as `true` or `false` to show or hide the headers at initial load. By default, the `showHeaders` property is enabled in each worksheet.

## Gridlines

Gridlines act as a border like appearance of cells. They are used to distinguish cells on the worksheet. You can dynamically show or hide gridlines by using one of the following ways,

* Switch to `View` tab, and then select `Hide Gridlines` option to hide the gridlines in worksheet.
* Set `showGridLines` property in `sheets` as `true` or `false` to show or hide the gridlines at initial load. By default, the `showGridLines` property is enabled in each worksheet.

The following code example shows the headers and gridlines operation in spreadsheet.

{% tab template="spreadsheet/headers-gridlines", sourceFiles="app.ts,index.html,datasource.ts", es5Template="es5-headers-gridlines", iframeHeight="450px" %}

```typescript
import { Spreadsheet, SheetModel, ColumnModel } from '@syncfusion/ej2-spreadsheet';
import { data } from './datasource.ts';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let columns: ColumnModel[] = [{ width: 150 }, { width: 110 }, { width: 110 }, { width: 85 }, { width: 85 }, { width: 85 }, { width: 85 },
        { width: 85 }];

let sheets: SheetModel[] = [{
    name: 'Price Details',
    ranges: [{ dataSource: data }],
    columns: columns,
    // Hiding the gridlines in `Price Details` sheet
    showGridLines: false,
    // Hiding the headers in `Price Details` sheet
    showHeaders: false
}];

let spreadsheet: Spreadsheet = new Spreadsheet({
    sheets: sheets,
    created: (): void => {
        spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center' }, 'A1:H1');
        spreadsheet.cellFormat({ textAlign: 'center' }, 'D2:H11');
        // The gridlines have been removed to set border for the range of cells
        spreadsheet.setBorder({ border: '1px solid #e0e0e0' }, 'A1:H11');
    },
    // Removed the unwanted support for this samples
    showFormulaBar: false, showSheetTabs: false
});

spreadsheet.appendTo('#spreadsheet');
```

{% endtab %}

## Sheet visibility

Hiding a worksheet can help prevent unauthorized or accidental changes to your file.

There are three visibility state as like Microsoft Excel,

| State | Description |
|-------|---------|
| `Visible` | You can see the worksheet once the component is loaded. |
| `Hidden` | This worksheet is not visible, but you can unhide by selecting the sheet from `List All Sheets` dropdown menu. |
| `VeryHidden` | This worksheet is not visible and cannot be unhidden. Changing the state property to `Visible` is the only way to view this sheet. |

The following code example shows the three types of sheet visibility state.

{% tab template="spreadsheet/sheet-visibility", sourceFiles="app.ts,index.html,datasource.ts", es5Template="es5-sheet-visibility", iframeHeight="450px" %}

```typescript
import { Spreadsheet, SheetModel } from '@syncfusion/ej2-spreadsheet';
import { enableRipple } from '@syncfusion/ej2-base';
import { data } from './datasource.ts';

enableRipple(true);

let sheets: SheetModel[] = [{
    name: 'Visible Sheet',
    ranges: [{ dataSource: data }],
    columns: [{ width: 150 }, { width: 110 }, { width: 110 }, { width: 85 }, { width: 85 }, { width: 85 }, { width: 85 },
        { width: 85 }],
    // By default, state is set as `visible`. We don’t  need to said it in the sample
    state: 'Visible'
},
{
    name: 'Very Hidden Sheet',
    ranges: [{ dataSource: data }],
    columns: [{ width: 150 }, { width: 110 }, { width: 110 }, { width: 85 }, { width: 85 }, { width: 85 }, { width: 85 },
        { width: 85 }],
    // Sets sheet state as `VeryHidden`. It can't be unhidden.
    state: 'VeryHidden'
},
{
    name: 'Hidden Sheet',
    ranges: [{ dataSource: data }],
    columns: [{ width: 150 }, { width: 110 }, { width: 110 }, { width: 85 }, { width: 85 }, { width: 85 }, { width: 85 },
        { width: 85 }],
    // Sets sheet state as `Hidden`. It can be unhidden dynamically.
    state: 'Hidden'
}];

let spreadsheet: Spreadsheet = new Spreadsheet({
    sheets: sheets,
    created: (): void => {
        // Applies style formatting to active visible sheet
        spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center' }, 'A1:H1');
        spreadsheet.cellFormat({ textAlign: 'center' }, 'D2:H11');
        // Applies style formatting to active hidden sheet
        spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center' }, 'Hidden Sheet!A1:H1');
        spreadsheet.cellFormat({ textAlign: 'center' }, 'Hidden Sheet!D2:H11');
    },
    openUrl: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/open',
    saveUrl: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/save',
    // Removed the unwanted support for this samples
    showFormulaBar: false, showRibbon: false
});

spreadsheet.appendTo('#spreadsheet');
```

{% endtab %}

## See Also

* [Sheet protection](./protect-sheet)
* [Rows and columns](./rows-and-columns)
* [Cell range](./cell-range)
* [Formatting](./formatting)
