---
title: "Hyperlink"
component: "Spreadsheet"
description: "This section helps to learn how to insert, edit and remove a hyperlink in Spreadsheet control."
---

# Hyperlink

Hyperlink is used to navigate to web links or cell reference within the sheet or to other sheets in Spreadsheet. You can use the [`allowHyperlink`](../api/spreadsheet/#allowHyperlink) property to enable or disable hyperlink functionality.

> * The default value for `allowHyperlink` property is `true`.

## Insert Link

You can insert a hyperlink in a worksheet cell for quick access to related information.

### User Interface

In the active spreadsheet, click the cell where you want to create a hyperlink. Insert hyperlink can be done by any of the following ways:

* Select the INSERT tab in the Ribbon toolbar and choose the `Link` item.
* Right-click the cell and then click Hyperlink item in the context menu.
* Use `Ctrl + K` keyboard shortcut to apply the hyperlink.
* Use the [`addHyperlink`](../api/spreadsheet/#hyperlink) method programmatically.

## Edit Hyperlink

You can change an existing hyperlink in your workbook by changing its destination or the text that is used to represent it.

### User Interface

In the active spreadsheet, Select the cell that contains the hyperlink that you want to change. Editing the hyperlink while opening the dialog can be done by any one of the following ways:

* Select the INSERT tab in the Ribbon toolbar and choose the `Link` item.
* Right-click the cell and then click Edit Hyperlink item in the context menu, or you can press Ctrl+K.

In the Edit Link dialog box, make the changes that you want, and click UPDATE.

## Remove Hyperlink

Performing this operation remove a single hyperlink without losing the display text.

### User Interface

In the active spreadsheet, click the cell where you want to remove a hyperlink. remove hyperlink can be done by any of the following ways:
* Right-click the cell and then click Remove Hyperlink item in the context menu.
* Use the [`removeHyperlink()`](../api/spreadsheet/#hyperlink) method programmatically.

## How to change target attribute

There is an event named `beforeHyperlinkClick` which triggers only on clicking hyperlink. You can customize where to open the hyperlink by using the `target` property in the arguments of that event.

{% tab template="spreadsheet/link", sourceFiles="app.ts,index.html", es5Template="es5-hyperlink", iframeHeight="450px" , isDefaultActive=true %}

```typescript

import { Spreadsheet } from '@syncfusion/ej2-spreadsheet';

let sheet: SheetModel[] = [
    {
        name: 'PriceDetails'
        rows: [
            {
                cells: [
                    { value: 'Item Name' },
                    { value: 'Stock Detail' },
                    { value: 'Website' }
                ]
            },
            {
                cells: [
                    { value: 'Casual Shoes' },
                    { value: 'OUT OF STOCK' },
                    { value: 'Amazon', hyperlink: 'https://www.amazon.com/' }
                ]
            },
            {
                cells: [
                    { value: 'Sports Shoes' },
                    { value: 'IN STOCK', hyperlink: 'Stock!A2:B2'},
                    { value: 'Overstack', hyperlink: 'https://www.overstock.com/' }
                ]
            },
            {
                cells: [
                    { value: 'Formal Shoes' },
                    { value: 'IN STOCK', hyperlink: 'Stock!A3:B3'},
                    { value: 'AliExpress', hyperlink: 'https://www.aliexpress.com/' }
                ]
            },
            {
                cells: [
                    { value: 'Sandals & Floaters' },
                    { value: 'OUT OF STOCK'},
                    { value: 'AliBaba', hyperlink: 'http://www.alibaba.com/' }
                ]
            },
            {
                cells: [
                    { value: 'Flip-Flops & Slippers' },
                    { value: 'IN STOCK', hyperlink: 'Stock!A4:B4' },
                    { value: 'Taobao', hyperlink: 'https://taobao.com/' }
                ]
            },
        ],
        columns: [
            { width: 160 }, { width: 160 }, { width: 120 }
        ]
    },
{
    name: 'Stock',
    rows: [
            {
                cells: [
                    { value: 'Item Name' },
                    { value: 'Available Count' },
                ]
            },
            {
                cells: [
                    { value: 'Sports Shoes' },
                    { value: '30' },
                ]
            },
            {
                cells: [
                    { value: 'Formal Shoes' },
                    { value: '25' },
                ]
            },
            {
                cells: [
                    { value: 'Flip-Flops & Slippers' },
                    { value: '40' },
                ]
            },
            {
                cells: [
                    { value: 'Running Shoes' },
                    { value: '25' },
                ]
            },
        ],
        columns: [
            { width: 160 }, { width: 120 }
        ]
}
];

//Initialize the SpreadSheet control
let spreadsheet: Spreadsheet = new Spreadsheet({
  sheets: sheet,
  beforeHyperlinkClick: (args: BeforeHyperlinkArgs) => {
        args.target = '_self'; //change target attribute
    }
});
spreadsheet.appendTo('#spreadsheet');
```

{% endtab %}

## See Also

* [Sorting](./sort)
* [Filtering](./filter)
* [Undo Redo](./undo-redo)