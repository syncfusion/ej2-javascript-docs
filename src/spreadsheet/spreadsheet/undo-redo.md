---
title: "Undo Redo"
component: "Spreadsheet"
description: "This section helps you to revert the last action performed and revert the last undo action performed with Spreadsheet."
---

# Undo and Redo

`Undo` option helps you to undone the last action performed and `Redo` option helps you to do the same action which is reverted in the Spreadsheet. You can use the [`allowUndoRedo`](../api/spreadsheet/#allowundoredo) property to enable or disable undo redo functionality in spreadsheet.

> * The default value for `allowUndoRedo` property is `true`.

By default, the `UndoRedo` module is injected internally into Spreadsheet to perform undo redo.

## Undo

It reverses the last action you performed with Spreadsheet. Undo can be done by any of the following ways:

* Select the undo item from HOME tab in Ribbon toolbar.
* Use `Ctrl + Z` keyboard shortcut to perform the undo.
* Use the [`undo`](../api/spreadsheet/#undo) method programmatically.

## Redo

It reverses the last undo action you performed with Spreadsheet. Redo can be done by any of the following ways:

* Select the redo item from HOME tab in Ribbon toolbar.
* Use `Ctrl + Y` keyboard shortcut to perform the redo.
* Use the [`redo`](../api/spreadsheet/#redo) method programmatically.

## Update custom actions in UndoRedo collection

You can update your own custom actions in UndoRedo collection, by using the [`updateUndoRedoCollection`](../api/spreadsheet/#updateUndoRedoCollection) method. And also customize the undo redo operations of your custom action by using `actionComplete` event.

The following code example shows `How to update and customize your own actions for undo redo` functionality in the Spreadsheet control.

{% tab template="spreadsheet/undo-redo", sourceFiles="app.ts,index.html", es5Template="es5-undo-redo", iframeHeight="450px", isDefaultActive=true %}

```typescript

import { Spreadsheet, getRangeIndexes, ColumnModel } from '@syncfusion/ej2-spreadsheet';
import { defaultData } from './datasource.ts';
import { enableRipple, addClass, removeClass } from '@syncfusion/ej2-base';

let columns: ColumnModel[] = [
    {
        width: 130
    },
    {
        width: 92
    },
    {
        width: 96
    }
];

let spreadsheet: Spreadsheet = new Spreadsheet({
    sheets: [{ ranges: [{ dataSource: defaultData }], columns: columns }],
    actionComplete: (args): void => {
        let actionEvents: any = args;
        if (actionEvents.eventArgs.action == "customCSS") {
            let Element:HTMLElement = spreadsheet.getCell(actionEvents.eventArgs.rowIdx,actionEvents.eventArgs.colIdx);
            if (actionEvents.eventArgs.requestType == "undo") {
                removeClass([Element],'customClass'); // To remove the custom class in undo action
            }
            else {
                addClass([Element],'customClass');// To add the custom class in redo action
            }
        }
    }
});

//Render the initialized Spreadsheet
spreadsheet.appendTo('#spreadsheet');
document.getElementById("customBtn").addEventListener('click', updateCollection);

function updateCollection() {
    let cell: string = spreadsheet.getActiveSheet().activeCell;
    let cellIdx: number[] = getRangeIndexes(cell);
    let Element: HTMLElement = spreadsheet.getCell(cellIdx[0], cellIdx[1]);
    if (!Element.classList.contains("customClass")) {
        addClass([Element], 'customClass'); // To add the custom class in active cell element
        spreadsheet.updateUndoRedoCollection({ eventArgs: { class: 'customClass', rowIdx: cellIdx[0], colIdx: cellIdx[1], action: 'customCSS' } }); // To update the undo redo collection
    }
}
```

{% endtab %}

## See Also

* [Sorting](./sort)
* [Filtering](./filter)
* [Hyperlink](./link)