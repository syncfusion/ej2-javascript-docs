---
title: "Open and Save"
component: "Spreadsheet"
description: "This section helps to learn how to open and save excel file in Spreadsheet control"
---

# Open and Save

The native data format for Spreadsheet is `JSON`. When you open an excel file, it needs to be read and converted to client side Spreadsheet model. The converted client side Spreadsheet model is sent as JSON which is used to render Spreadsheet. Similarly, when you save the Spreadsheet, the client Spreadsheet model is sent to the server as JSON for processing and saved as Excel file formats. [`Server configuration`](./open-save/#server-configuration) is used for this process.

## Open

The Spreadsheet control opens an Excel document with its data, style, format, and more. To enable this feature, set [`allowOpen`](../api/spreadsheet/#allowopen) as `true` and assign service url to the [`openUrl`](../api/spreadsheet/#openurl) property.

**User Interface**:

In user interface you can open an Excel document by clicking `File > Open` menu item in ribbon.

The following code example shows `Open` option in the Spreadsheet control.

{% tab template="spreadsheet/open-save",sourceFiles="app.ts,index.html", es5Template="es5-open",iframeHeight="450px", isDefaultActive=true %}

```typescript

import { Spreadsheet } from '@syncfusion/ej2-spreadsheet';

//Initialize the Spreadsheet control
let spreadsheet: Spreadsheet = new Spreadsheet({
    allowOpen: true,
    openUrl: 'https://ej2services.syncfusion.com/development/web-services/api/spreadsheet/open'
});

//Render the initialized Spreadsheet
spreadsheet.appendTo('#spreadsheet');
```

{% endtab %}

> * Use `Ctrl + O` keyboard shortcut to open Excel documents.
> * The default value of the [allowOpen](../api/spreadsheet/#allowopen) property is `true`. For demonstration purpose, we have showcased the [allowOpen](../api/spreadsheet/#allowopen) property in previous code snippet.

## Save

The Spreadsheet control saves its data, style, format, and more as Excel file document. To enable this feature, set [`allowSave`](../api/spreadsheet/#allowsave) as `true` and assign service url to the [`saveUrl`](../api/spreadsheet/#saveurl) property.

**User Interface**:

In user interface, you can save Spreadsheet data as Excel document by clicking `File > Save As` menu item in ribbon.

The following code example shows `Save` option in the Spreadsheet control.

{% tab template="spreadsheet/open-save", sourceFiles="app.ts,index.html", es5Template="es5-save", iframeHeight="450px" %}

```typescript

import { Spreadsheet, SheetModel } from '@syncfusion/ej2-spreadsheet';
let sheet: SheetModel[] = [{
        rows: [{
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

### Methods

To save the Spreadsheet document as an `xlsx, xls, csv, or pdf` file, by using [save](../api/spreadsheet/#save) method should be called with the `url`, `fileName` and `saveType` as parameters. The following code example shows to save the spreadsheet file as an `xlsx, xls, csv, or pdf` in the button click event.

{% tab template="spreadsheet/save", sourceFiles="app.ts,index.html", es5Template="es5-save", iframeHeight="450px" %}

```typescript

import { Spreadsheet, ColumnModel } from '@syncfusion/ej2-spreadsheet';
import { Button } from '@syncfusion/ej2-buttons';
import { data } from './datasource.ts';

let columns: ColumnModel[] = [{ width: 100 }, { width: 130 },{ width: 96},
    { width: 130 }, { width: 130 },{ width: 96},
    { width: 100 }, { width: 100 },{ width: 110}, { width: 100 }, { width: 130 },{ width: 150}]

let spreadsheet: Spreadsheet = new Spreadsheet({
    sheets: [{ ranges: [{ dataSource: data }], columns: columns }],
    allowSave: true
});

//Render the initialized Spreadsheet
spreadsheet.appendTo('#spreadsheet');

let button: Button = new Button({content: 'Save As xlsx'});
button.appendTo('#xlsx');
let button1: Button = new Button({content: 'Save As xls'});
button1.appendTo('#xls');
let button2: Button = new Button({content: 'Save As csv'});
button2.appendTo('#csv');
let button3: Button = new Button({content: 'Save As pdf'});
button3.appendTo('#pdf');
document.getElementById('xlsx').onclick = (): void => {
  spreadsheet.save({url: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/save', fileName: "Sample", saveType: "Xlsx"});
}
document.getElementById('xls').onclick = (): void => {
  spreadsheet.save({url: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/save', fileName: "Sample", saveType: "Xls"});
}
document.getElementById('csv').onclick = (): void => {
  spreadsheet.save({url: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/save',fileName: "Sample", saveType: "Csv"});
}
document.getElementById('pdf').onclick = (): void => {
  spreadsheet.save({url: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/save',fileName: "Sample", saveType: "Pdf"});
}
```

{% endtab %}

## Server Configuration

Import and export are processed in `server-side` using Spreadsheet server library. The following code snippets shows server configuration using `WebAPI` service,

```csharp

    [Route("api/[controller]")]
    public class SpreadsheetController : Controller
    {
        //To open excel file
        [AcceptVerbs("Post")]
        [HttpPost]
        [EnableCors("AllowAllOrigins")]
        [Route("Open")]
        public IActionResult Open(IFormCollection openRequest)
        {
            OpenRequest open = new OpenRequest();
            open.File = openRequest.Files[0];
            return Content(Workbook.Open(open));
        }

        //To save as excel file
        [AcceptVerbs("Post")]
        [HttpPost]
        [EnableCors("AllowAllOrigins")]
        [Route("Save")]
        public IActionResult Save(SaveSettings saveSettings)
        {
            return Workbook.Save(saveSettings);
        }
    }
```

## Server Dependencies

Open and save helper functions are shipped in the Syncfusion.EJ2.Spreadsheet package, which is available in Essential Studio and [`nuget.org`](https://www.nuget.org/). Following list of dependencies required for Spreadsheet open and save operations.

* Syncfusion.EJ2
* Syncfusion.EJ2.Spreadsheet
* Syncfusion.Compression.Base
* Syncfusion.XlsIO.Base

## Supported File Formats

The following list of Excel file formats are supported in Spreadsheet:

* MS Excel (.xlsx)
* MS Excel 97-2003 (.xls)
* Comma Separated Values (.csv)
* Portable Document Format (.pdf)

## See Also

* [Filtering](./filter)
* [Sorting](./sort)
* [Hyperlink](./link)