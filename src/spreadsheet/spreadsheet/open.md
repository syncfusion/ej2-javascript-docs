---
title: "Open"
component: "Spreadsheet"
description: "This section helps to learn how to open excel file in Spreadsheet control"
---

# Open

The Spreadsheet control opens an Excel document with its data, style, format, and more. To enable this feature, set [`allowOpen`](../api/spreadsheet/#allowopen) to `true` and assign service url to the [`openUrl`](../api/spreadsheet/#openurl) property.

The following list of Excel file formats are supported in Spreadsheet:

* MS Excel (.xlsx)
* MS Excel 97-2003 (.xls)
* Comma Separated Values (.csv)

## User Interface

In user interface you can open an Excel document by clicking `File > Open` menu item in ribbon.

The following code example shows `Open` option in the Spreadsheet control.

{% tab template="spreadsheet/open",sourceFiles="app.ts,index.html", es5Template="open",iframeHeight="450px", isDefaultActive=true %}

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