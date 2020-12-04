---
title: "Formulas"
component: "Spreadsheet"
description: "This section helps you to understand the formula feature in the Essential JS 2 spreadsheet."
---

# Formulas

Formulas are used for calculating the data in a worksheet. You can refer the cell reference from same sheet or from different sheets.

## Usage

You can set formula for a cell in the following ways,

* Using the `formula` property from `cell`, you can set the formula or expression to each cell at initial load.
* Set the formula or expression through data binding.
* You can set formula for a cell by [`editing`](./editing).
* Using the [`updateCell`](../api/spreadsheet/#updatecell) method, you can set or update the cell formula.

## User Defined Functions

The list of formulas supported in the spreadsheet is sufficient for most of your calculations. If not, you can add your own custom function using the [`addCustomFunction`](../api/spreadsheet/#addcustomfunction) method. Use [`computeExpression`](../api/spreadsheet/#computeexpression) method, if you want to compute any formula or expression.

The following code example shows the calculation of data using supported and custom `formulas` in the spreadsheet.

{% tab template="spreadsheet/formula", sourceFiles="app.ts,index.html,datasource.ts", es5Template="es5-formula", iframeHeight="450px", isDefaultActive=true %}

```typescript
import { Spreadsheet, SheetModel, ColumnModel, RowModel } from '@syncfusion/ej2-spreadsheet';
import { data } from './datasource.ts';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let columns: ColumnModel[] = [{ width: 150 }, { width: 120 }, { width: 120 }, { width: 120 }, { width: 120 }];

let rows: RowModel[] = [
    {
        height: 40, customHeight: true, cells: [{ value: 'Monthly Expense', colSpan: 5, style:
        { textAlign: 'center', fontWeight: 'bold', verticalAlign: 'middle', fontStyle: 'italic', fontSize: '15pt' } }]
    },
    { height: 30 },
    {
        index: 11, cells: [{ value: 'Totals', style: { fontStyle: 'italic', fontWeight: 'bold' } }, { formula: '=SUM(B3:B11)' },
            // Calculating total of each column data through cell binding.
            { formula: '=SUM(C3:C11)' }, { formula: '=SUM(D3:D11)' }]
    },
    {
        cells: [{ index: 1, value: 'Number of Categories', colSpan: 2, style: { fontWeight: 'bold', textAlign: 'right' } },
            { index: 3, formula: '=COUNTA(A3:A11)' }]
    },
    {
        cells: [{ index: 1, value: 'Average Spend', colSpan: 2, style: { fontWeight: 'bold', textAlign: 'right' } },
            { index: 3, formula: '=AVERAGE(B3:B11)', format: '$#,##0' }]
    },
    {
        cells: [{ index: 1, value: 'Min Spend', colSpan: 2, style: { fontWeight: 'bold', textAlign: 'right' } },
            { index: 3, formula: '=MIN(B3:B11)', format: '$#,##0' }]
    },
    {
        cells: [{ index: 1, value: 'Max Spend', colSpan: 2, style: { fontWeight: 'bold', textAlign: 'right' } },
            { index: 3, formula: '=MAX(B3:B11)', format: '$#,##0' }]
    }
];

let sheets: SheetModel[] = [{ ranges: [{ dataSource: data, startCell: 'A2' }], columns: columns, rows }];

// Custom function to calculate percentage between two cell values.
function calculatePercentage(firstCell: string, secondCell: string): number {
    return Number(firstCell) / Number(secondCell);
}

let spreadsheet: Spreadsheet = new Spreadsheet({
    sheets: sheets,
    created: (): void => {
        spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center' }, 'A2:E2');
        spreadsheet.numberFormat('$#,##0', 'B3:D12');
        spreadsheet.numberFormat('0%', 'E3:E12');

        // Adding custom function for calculating the percentage between two cells.
        spreadsheet.addCustomFunction(calculatePercentage, 'PERCENTAGE');
        // Calculate percentage using custom added formula in E12 cell.
        spreadsheet.updateCell({ formula: '=PERCENTAGE(C12,D12)' }, 'E12');
    },
    showRibbon: false, showSheetTabs: false
});

spreadsheet.appendTo('#spreadsheet');
```

{% endtab %}

## Formula bar

Formula bar is used to edit or enter cell data in much easier way. By default, the formula bar is enabled in the spreadsheet. Use the [`showFormulaBar`](../api/spreadsheet/#showformulabar) property to enable or disable the formula bar.

## Named Ranges

You can define a meaningful name for a cell range and use it in the formula for calculation. It makes your formula much easier to understand and maintain. You can add named ranges to the Spreadsheet in the following ways,

* Using the [`definedNames`](../api/spreadsheet/#definednames) collection, you can add multiple named ranges at initial load.
* Use the [`addDefinedName`](../api/spreadsheet/#adddefinedname) method to add a named range dynamically.
* You can remove an added named range dynamically using the [`removeDefinedName`](../api/spreadsheet/#removedefinedname) method.
* Select the range of cells, and then enter the name for the selected range in the name box.

The following code example shows the usage of named ranges support.

{% tab template="spreadsheet/defined-name", sourceFiles="app.ts,index.html,datasource.ts", es5Template="es5-defined-name", iframeHeight="450px" %}

```typescript
import { Spreadsheet, SheetModel, ColumnModel, RowModel, DefineNameModel } from '@syncfusion/ej2-spreadsheet';
import { data } from './datasource.ts';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let columns: ColumnModel[] = [{ width: 150 }, { width: 120 }, { width: 120 }, { width: 120 }, { width: 120 }];

// Setting names for `categories`, `monthly spendings` and `annual spendings` ranges.
let definedNames: DefineNameModel[] = [
    { name: 'Categories', refersTo: '=Budget Details!A3:A11' },
    { name: 'MonthlySpendings', refersTo: '=Budget Details!B3:B11' },
    { name: 'AnnualSpendings', refersTo: '=Budget Details!C3:C11' }
];

let rows: RowModel[] = [
    {
        height: 40, customHeight: true, cells: [{ value: 'Monthly Expense', colSpan: 5, style:
        { textAlign: 'center', fontWeight: 'bold', verticalAlign: 'middle', fontStyle: 'italic', fontSize: '15pt' } }]
    },
    { height: 30 },
    {
        index: 11, cells: [{ value: 'Totals', style: { fontStyle: 'italic', fontWeight: 'bold' } }, { formula: '=SUM(MonthlySpendings)' },
            // Initializing the formulas using defined names.
            { formula: '=SUM(AnnualSpendings)' }, { formula: '=SUM(LastYearSpendings)' }, { formula: '=C12/D12' }]
    },
    {
        cells: [{ index: 1, value: 'Number of Categories', colSpan: 2, style: { fontWeight: 'bold', textAlign: 'right' } },
            { index: 3, formula: '=COUNTA(Categories)' }]
    },
    {
        cells: [{ index: 1, value: 'Average Spend', colSpan: 2, style: { fontWeight: 'bold', textAlign: 'right' } },
            { index: 3, formula: '=AVERAGE(MonthlySpendings)', format: '$#,##0' }]
    },
    {
        cells: [{ index: 1, value: 'Min Spend', colSpan: 2, style: { fontWeight: 'bold', textAlign: 'right' } },
            { index: 3, formula: '=MIN(MonthlySpendings)', format: '$#,##0' }]
    },
    {
        cells: [{ index: 1, value: 'Max Spend', colSpan: 2, style: { fontWeight: 'bold', textAlign: 'right' } },
            { index: 3, formula: '=MAX(MonthlySpendings)', format: '$#,##0' }]
    }
];

let sheets: SheetModel[] = [{ name: 'Budget Details', ranges: [{ dataSource: data, startCell: 'A2' }], columns: columns, rows }];
let spreadsheet: Spreadsheet = new Spreadsheet({
    sheets: sheets,
    definedNames: definedNames,
    beforeDataBound: (): void => {
        // Adding name dynamically for `last year spending` and `percentage change` ranges.
        spreadsheet.addDefinedName({ name: 'LastYearSpendings', refersTo: '=D3:D11' });
        spreadsheet.addDefinedName({ name: 'PercentageChange', refersTo: '=E3:E11' });
    },
    created: (): void => {
        // Removing the unwanted `PercentageChange` named range
        spreadsheet.removeDefinedName('PercentageChange', '');

        spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center' }, 'A2:E2');
        spreadsheet.numberFormat('$#,##0', 'B3:D12');
        spreadsheet.numberFormat('0%', 'E3:E12');
    },
    showRibbon: false, showSheetTabs: false
});

spreadsheet.appendTo('#spreadsheet');
```

{% endtab %}

## Supported Formulas

The following are the list of formulas supported in spreadsheet,

| Formula | Description |
|-------|---------|
| ABS | Returns the value of a number without its sign. |
| AND | Returns TRUE if all the arguments are TRUE, otherwise returns FALSE. |
| AVERAGE | Calculates average for the series of numbers and/or cells excluding text. |
| AVERAGEA | Calculates the average for the cells evaluating TRUE as 1, text and FALSE as 0. |
| AVERAGEIF | Clears content of the active cell and enables edit mode. |
| AVERAGEIFS | Calculates average for the cells based on specified conditions. |
| CEILING | Rounds a number up to the nearest multiple of a given factor. |
| CHOOSE | Returns a value from list of values, based on index number. |
| CONCAT | Concatenates a list or a range of text strings. |
| CONCATENATE | Combines two or more strings together. |
| COUNT | Counts the cells that contain numeric values in a range. |
| COUNTA | Counts the cells that contains values in a range. |
| COUNTIF | Counts the cells based on specified condition. |
| COUNTIFS | Counts the cells based on specified conditions. |
| DATE | Returns the date based on given year, month, and day. |
| DAY | Returns the day from the given date. |
| DAYS | Returns the number of days between two dates. |
| FIND | Returns the position of a string within another string, which is case sensitive.|
| FLOOR | Rounds a number down to the nearest multiple of a given factor. |
| IF | Returns value based on the given expression. |
| IFERROR | Returns value if no error found else it will return specified value. |
| IFS | Returns value based on the given multiple expressions. |
| INDEX | Returns a value of the cell in a given range based on row and column number. |
| INTERCEPT | Calculates the point of the Y-intercept line via linear regression. |
| LN | Returns the natural logarithm of a number. |
| MATCH | Returns the relative position of a specified value in given range. |
| MAX | Returns the largest number of the given arguments. |
| MIN | Returns the smallest number of the given arguments. |
| OR | Returns TRUE if any of the arguments are TRUE, otherwise returns FALSE. |
| PRODUCT | Multiplies a series of numbers and/or cells. |
| RADIANS | Converts degrees into radians. |
| RAND | Returns a random number between 0 and 1. |
| RANDBETWEEN | Returns a random integer based on specified values. |
| SLOPE | Returns the slope of the line from linear regression of the data points. |
| SUBTOTAL | Returns subtotal for a range using the given function number. |
| SUM | Adds a series of numbers and/or cells. |
| SUMIF | Adds the cells based on specified condition. |
| SUMIFS | Adds the cells based on specified conditions. |

## See Also

* [Editing](./editing)
* [Formatting](./formatting)
* [Open](./open)
* [Save](./save)
