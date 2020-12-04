---
title: "Save"
component: "Spreadsheet"
description: "This section helps to learn how to save Spreadsheet data as excel file document."
---

# Save

The Spreadsheet control saves its data, style, format, and more as Excel file document. To enable this feature, set [`allowSave`](../api/spreadsheet/#allowsave) to `true` and assign service url to the [`saveUrl`](../api/spreadsheet/#saveurl) property.

The following list of Excel file formats are supported in Spreadsheet:

* MS Excel (.xlsx)
* MS Excel 97-2003 (.xls)
* Comma Separated Values (.csv)

## User Interface

In user interface, you can save Spreadsheet data as Excel document by clicking `File > Save As` menu item in ribbon.

The following code example shows `Save` option in the Spreadsheet control.

{% tab template="spreadsheet/save", sourceFiles="app.ts,index.html", es5Template="save", iframeHeight="450px", isDefaultActive=true %}

```typescript

import { Spreadsheet, SheetModel } from '@syncfusion/ej2-spreadsheet';
let sheet: SheetModel[] = [{
        rows: [{
                index: 0,
                cells: [
                    { index: 0, value: 'Order ID',  style: { fontWeight: 'bold' }},
                    { value: 'Customer ID', style: { fontWeight: 'bold' }},
                    { value: 'Employee ID', style: { fontWeight: 'bold' }},
                    { value: 'Ship Name', style: { fontWeight: 'bold' }},
                    { value: 'Ship City', style: { fontWeight: 'bold' }},
                    { value: 'Ship Address', style: { fontWeight: 'bold' }}
                ]
            },
            {
                cells: [
                    { value: '10248' },
                    { value: 'VINET' },
                    { value: '5' },
                    { value: 'Vins et alcools Chevalier' },
                    { value: 'Reims' },
                    { value: '59 rue de lAbbaye' }
                ]
            },
            {
                cells: [
                    { value: '10249' },
                    { value: 'TOMSP' },
                    { value: '6' },
                    { value: 'Toms Spezialitäten' },
                    { value: 'Münster' },
                    { value: 'Luisenstr. 48' }
                ]
            },
            {
                cells: [
                    { value: '10250' },
                    { value: 'HANAR' },
                    { value: '4' },
                    { value: 'Hanari Carnes' },
                    { value: 'Rio de Janeiro' },
                    { value: 'Rua do Paço, 67' }
                ]
            },
            {
                cells: [
                    { value: '10251' },
                    { value: 'VICTE' },
                    { value: '3' },
                    { value: 'Victuailles en stock' },
                    { value: 'Lyon' },
                    { value: '2, rue du Commerce' }
                ]
            }],
    columns: [
            { width: 80 }, { width: 80 }, { width: 82 },
            { width: 160 }, { width: 110 }, { width: 130 }
        ]
}];
//Initialize the Spreadsheet control
let spreadsheet: Spreadsheet = new Spreadsheet({
    sheets: sheet,
    allowSave: true,
    saveUrl: 'https://ej2services.syncfusion.com/development/web-services/api/spreadsheet/save'
});
//Render the initialized Spreadsheet
spreadsheet.appendTo('#spreadsheet');
```

{% endtab %}

> * Use `Ctrl + S` keyboard shortcut to save the Spreadsheet data as Excel file.
> * The default value of [allowSave](../api/spreadsheet/#allowsave) property is `true`. For demonstration purpose, we have showcased the [allowSave](../api/spreadsheet/#allowsave) property in previous code snippet.