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

The following sample shows the `Open` option by using the [`openUrl`](../api/spreadsheet/#openUrl) property in the Spreadsheet control. You can also use the [`beforeOpen`](../api/spreadsheet/#beforeOpen) event to trigger before opening an Excel file.

{% tab template="spreadsheet/open-save",sourceFiles="app.ts,index.html", es5Template="es5-open",iframeHeight="450px", isDefaultActive=true %}

```typescript

import { Spreadsheet, BeforeOpenEventArgs } from '@syncfusion/ej2-spreadsheet';

//Initialize the Spreadsheet control
let spreadsheet: Spreadsheet = new Spreadsheet({
    allowOpen: true,
    openUrl: 'https://ej2services.syncfusion.com/development/web-services/api/spreadsheet/open',
    beforeOpen: (args: BeforeOpenEventArgs) => {
        // your code snippets here
    }
});

//Render the initialized Spreadsheet
spreadsheet.appendTo('#spreadsheet');
```

{% endtab %}

Please find the below table for the beforeOpen event arguments.

 | **Parameter** | **Type** | **Description** |
| ----- | ----- | ----- |
| file | FileList or string or File | To get the file stream. `FileList` -  contains length and item index. <br/> `File` - specifies the file lastModified and file name. |
| cancel | boolean | To prevent the open operation. |
| requestData | object |  To provide the Form data. |

> * Use `Ctrl + O` keyboard shortcut to open Excel documents.
> * The default value of the [allowOpen](../api/spreadsheet/#allowopen) property is `true`. For demonstration purpose, we have showcased the [allowOpen](../api/spreadsheet/#allowopen) property in previous code snippet.

### Open an external URL excel file while initial load

You can achieve to access the remote excel file by using the [`created`](../api/spreadsheet/#created) event. In this event you can fetch the excel file and convert it to a blob. Convert this blob to a file and [`open`](../api/spreadsheet/#open) this file by using Spreadsheet component open method.

{% tab template="spreadsheet/open-save",sourceFiles="app.ts,index.html", es5Template="es5-openUrl",iframeHeight="450px" %}

```typescript

import { Spreadsheet } from '@syncfusion/ej2-spreadsheet';

//Initialize the Spreadsheet control
    let spreadsheet: Spreadsheet = new Spreadsheet({
        openUrl: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/open',
        saveUrl: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/save',
        created: (): void => {
            fetch("https://js.syncfusion.com/demos/ejservices/data/Spreadsheet/LargeData.xlsx") // fetch the remote url
                .then((response) => {
                    response.blob().then((fileBlob) => { // convert the excel file to blob
                    let file = new File([fileBlob], "Sample.xlsx"); //convert the blob into file
                    spreadsheet.open({ file: file }); // open the file into Spreadsheet
                    })
                })
        }
    });
//Render the initialized Spreadsheet
spreadsheet.appendTo('#spreadsheet');
```

{% endtab %}

## Save

The Spreadsheet control saves its data, style, format, and more as Excel file document. To enable this feature, set [`allowSave`](../api/spreadsheet/#allowsave) as `true` and assign service url to the [`saveUrl`](../api/spreadsheet/#saveurl) property.

**User Interface**:

In user interface, you can save Spreadsheet data as Excel document by clicking `File > Save As` menu item in ribbon.

The following sample shows the `Save` option by using the [`saveUrl`](../api/spreadsheet/#saveUrl) property in the Spreadsheet control. You can also use the [`beforeSave`](../api/spreadsheet/#beforeSave) event to trigger before saving the Spreadsheet as an Excel file.

{% tab template="spreadsheet/open-save", sourceFiles="app.ts,index.html", es5Template="es5-save", iframeHeight="450px" %}

```typescript

import { Spreadsheet, SheetModel, BeforeSaveEventArgs } from '@syncfusion/ej2-spreadsheet';
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
    saveUrl: 'https://ej2services.syncfusion.com/development/web-services/api/spreadsheet/save',
    beforeSave: (args: BeforeSaveEventArgs) => {
        // your code snippets here
    }
});
//Render the initialized Spreadsheet
spreadsheet.appendTo('#spreadsheet');
```

{% endtab %}

Please find the below table for the beforeSave event arguments.

| **Parameter** | **Type** | **Description** |
| ----- | ----- | ----- |
| url | string |  Specifies the save url.  |
| fileName | string | Specifies the file name. |
| saveType | SaveType | Specifies the saveType like Xlsx, Xls, Csv and Pdf. |
| customParams | object | Passing the custom parameters from client to server while performing save operation. |
| isFullPost | boolean | It sends the form data from client to server, when set to true. It fetches the data from client to server and returns the data from server to client, when set to false. |
| needBlobData | boolean | You can get the blob data if set to true. |
| cancel | boolean | To prevent the save operations. |

> * Use `Ctrl + S` keyboard shortcut to save the Spreadsheet data as Excel file.
> * The default value of [allowSave](../api/spreadsheet/#allowsave) property is `true`. For demonstration purpose, we have showcased the [allowSave](../api/spreadsheet/#allowsave) property in previous code snippet.
> * Demo purpose only, we have used the online web service url link.

### To send and receive custom params from client to server

Passing the custom parameters from client to server by using [`beforeSave`](../api/spreadsheet/#beforeSave) event.

{% tab template="spreadsheet/open-save", sourceFiles="app.ts,index.html", es5Template="es5-custom-params", iframeHeight="450px" %}

```typescript

import { Spreadsheet } from '@syncfusion/ej2-spreadsheet';
import { data } from './datasource.ts';

//Initialize the SpreadSheet control
let spreadsheet: Spreadsheet = new Spreadsheet({
  sheets: [{
                ranges: [{ dataSource: data }],
                columns: [{ width: 80 }, { width: 80 },{ width: 80},
                          { width: 160 }, { width: 100 }, {width: 150}]
            }],
            saveUrl: 'https://ej2services.syncfusion.com/development/web-services/api/spreadsheet/save',
            beforeSave: (args: BeforeSaveEventArgs) => {
               args.customParams = { customParams: 'you can pass custom params in server side'}; // you can pass the custom params
            }
  }
});
spreadsheet.appendTo('#spreadsheet');
```

{% endtab %}

Server side code snippets:

```csharp

    public IActionResult Save(SaveSettings saveSettings, string customParams)
        {
            Console.WriteLine(customParams); // you can get the custom params in controller side
            return Workbook.Save(saveSettings);
        }
```

### Methods

To save the Spreadsheet document as an `xlsx, xls, csv, or pdf` file, by using [`save`](../api/spreadsheet/#save) method should be called with the `url`, `fileName` and `saveType` as parameters. The following code example shows to save the spreadsheet file as an `xlsx, xls, csv, or pdf` in the button click event.

{% tab template="spreadsheet/save", sourceFiles="app.ts,index.html", es5Template="es5-save", iframeHeight="450px" %}

```typescript

import { Spreadsheet, ColumnModel } from '@syncfusion/ej2-spreadsheet';
import { data } from './datasource.ts';
import { DropDownButton, ItemModel } from "@syncfusion/ej2-splitbuttons";

//Initialize action items.
let items: ItemModel[] = [
  {
    text: "Save As xlsx"
  },
  {
    text: "Save As xls"
  },
  {
    text: "Save As csv"
  },
  {
    text: "Save As pdf"
  }
];

// Initialize the DropDownButton component.
let drpDownBtn: DropDownButton = new DropDownButton({
  items: items,
  cssClass: "e-round-corner",
  select: (args: MenuEventArgs) => {
    if (args.item.text === 'Save As xlsx')
      spreadsheet.save({url: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/save', fileName: "Sample", saveType: "Xlsx"});
    if (args.item.text === 'Save As xls')
      spreadsheet.save({url: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/save', fileName: "Sample", saveType: "Xls"});
    if (args.item.text === 'Save As csv')
      spreadsheet.save({url: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/save',fileName: "Sample", saveType: "Csv"});
    if (args.item.text === 'Save As pdf')
      spreadsheet.save({url: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/save',fileName: "Sample", saveType: "Pdf"});
  }
});

// Render initialized DropDownButton.
drpDownBtn.appendTo("#element");


let columns: ColumnModel[] = [{ width: 100 }, { width: 130 },{ width: 96},
    { width: 130 }, { width: 130 },{ width: 96},
    { width: 100 }, { width: 100 },{ width: 110}, { width: 100 }, { width: 130 },{ width: 150}]

let spreadsheet: Spreadsheet = new Spreadsheet({
    sheets: [{ ranges: [{ dataSource: data }], columns: columns }],
    allowSave: true
});

//Render the initialized Spreadsheet
spreadsheet.appendTo('#spreadsheet');
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