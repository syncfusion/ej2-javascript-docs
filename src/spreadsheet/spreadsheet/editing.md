---
title: "Editing"
component: "Spreadsheet"
description: "This section explains you about the editing feature in the Essential JS 2 spreadsheet."
---

# Editing

You can edit the contents of a cell directly in the cell or by typing in the formula bar. By default, the editing feature is enabled in the spreadsheet. Use the [`allowEditing`](../api/spreadsheet/#allowediting) property to enable or disable the editing feature.

## Edit cell

You can start editing by one of the following ways,

* Double click a cell to start the edit mode.
* Press `F2` key to edit the active cell.
* Use formula bar to perform editing.
* Use `BACKSPACE` or `SPACE` key to clear the cell content and start the edit mode.
* Using the [`startEdit`](../api/spreadsheet/#startedit) method.

## Save cell

If the cell is in editable state, you can save the edited cell by one of the following ways,

* Perform mouse click on any other cell rather than the current editing cell.
* Press `Enter` or `Tab` keys to save the edited cell content.
* Using the [`endEdit`](../api/spreadsheet/#endedit) method.

## Cancel editing

To cancel the editing without saving the changes, you can use one of the following ways,

* Press `ESCAPE` key, this will remove the editable state and update the unchanged cell content.
* Using the [`closeEdit`](../api/spreadsheet/#closeedit) method.

The following code example shows the editing operation in spreadsheet.

{% tab template="spreadsheet/editing", sourceFiles="app.ts,index.html,datasource.ts", es5Template="es5-editing", iframeHeight="450px", isDefaultActive=true %}

```typescript
import { Spreadsheet, SheetModel, ColumnModel, RowModel } from '@syncfusion/ej2-spreadsheet';
import { data } from './datasource.ts';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let columns: ColumnModel[] = [{ width: 120 }, { width: 180 }, { width: 100 }, { width: 120 }, { width: 120 }];

let rows: RowModel[] = [{
    index: 10, cells: [{ index: 3, value: 'Total Amount:', style: { fontWeight: 'bold' } }, { formula: '=SUM(E2:E10)' }]
}];

let sheets: SheetModel[] = [{ ranges: [{ dataSource: data }], columns: columns, selectedRange: 'E11', rows: rows }];

let spreadsheet: Spreadsheet = new Spreadsheet({
    sheets: sheets,
    created: (): void => {
        spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center' }, 'A1:E1');
        spreadsheet.cellFormat({ textAlign: 'center' }, 'A2:A10');
        spreadsheet.cellFormat({ textAlign: 'center' }, 'C2:C10');
        spreadsheet.numberFormat('$#,##0.00', 'D2:D10');
        spreadsheet.numberFormat('$#,##0.00', 'E2:E11');
    },
    // Triggers before going to the editing mode.
    cellEdit: (args: CellEditEventArgs): void => {
        // Preventing the editing in 5th(Amount) column.
        if (args.address.includes('E')) { args.cancel = true; }
    },
    // Trigger before saving the edited cell content.
    beforeCellSave: (args: CellEditEventArgs): void => {
        // Prevent saving the edited changes in 4th(Rate) column.
        if (args.address.includes('D')) {
            args.cancel = true;
            // Manually removes the editable state without saving the changes. Use `endEdit` method if you want to save the changes.
            spreadsheet.closeEdit();
        }
    },
    showSheetTabs: false, showRibbon: false
});

spreadsheet.appendTo('#spreadsheet');
```

{% endtab %}

## Limitation

* Text overflow in cells is not supported in Editing.

## See Also

* [Cell range](./cell-range)
* [Formatting](./formatting)
* [Hyperlink](./link)
* [Undo and Redo](./undo-redo)
* [Unlock the particular cells in the protected sheet](./protect-sheet#unlock-the-particular-cells-in-the-protected-sheet)
