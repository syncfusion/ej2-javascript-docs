---
title: "Data Binding"
component: "Spreadsheet"
description: "Learn how to bind local and remote data in the Essential JS 2 Spreadsheet control."
---

# Data Binding

The Spreadsheet uses [`DataManager`](../data), which supports both RESTful JSON data services and local JavaScript object array binding to a range. The `dataSource` property can be assigned either with the instance of [`DataManager`](../data) or JavaScript object array collection.

> To bind data to a cell, use `cell data binding` support.

## Local data

To bind local data to the Spreadsheet, you can assign a JavaScript object array to the `dataSource` property.

Refer to the following code example for local data binding.

{% tab template="spreadsheet/data-binding", sourceFiles="app.ts,index.html", es5Template="es5-local-data", iframeHeight="450px" , isDefaultActive=true %}

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
  }
});
spreadsheet.appendTo('#spreadsheet');
```

{% endtab %}

> The local data source can also be provided as an instance of the [`DataManager`](../data). By default, [`DataManager`](../data) uses [`JsonAdaptor`](../data/adaptors/#json-adaptor) for local data-binding.

## Remote data

To bind remote data to the Spreadsheet control, assign service data as an instance of [`DataManager`](../data) to the `dataSource` property. To interact with remote data source, provide the service endpoint `url`.

Refer to the following code example for remote data binding.

{% tab template="spreadsheet/data-binding", sourceFiles="app.ts,index.html", es5Template="es5-remote-data", iframeHeight="450px" %}

```typescript

import { DataManager, ODataAdaptor } from '@syncfusion/ej2-data';
import { Spreadsheet } from '@syncfusion/ej2-spreadsheet';

class CustomAdaptor extends ODataAdaptor {
    public processResponse(): Object {
        let result: Object[] = [];
        let original: { result: Object[], count: number } = super.processResponse.apply(this, arguments);
        original.result.forEach((item: { SNo: number }, idx: number) => {
            result[idx] = {};
            Object.keys(item).forEach((key: string) => {
                if (['OrderID', 'CustomerID', 'ShipName', 'ShipCity', 'ShipCountry'].indexOf(key) > -1) {
                    result[idx][key] = item[key];
                }
            });
        });
        return { result: result, count: original.count };
    }
}
    //Initialize DataManager
    let data: DataManager = new DataManager({
        //Remote service url
        url: 'https://ej2services.syncfusion.com/production/web-services/api/Orders',
        adaptor: new CustomAdaptor,
        crossDomain: true
    });

    //Initialize Spreadsheet control
    let spreadsheet: Spreadsheet = new Spreadsheet({
        sheets: [
            {
                rows: [{
                     cells: [{ value: 'Order ID' }, { value: 'Customer Name' }, { value: 'Ship Name' },
                    { value: 'Ship City' }, { value: 'Ship Country' }]
                }],
                ranges: [{ dataSource: data, showFieldAsHeader: false, startCell: 'A2' }],
                columns: [
                    { width: 80 }, { width: 100 }, { width: 82 },
                    { width: 160 }, { width: 110 }, { width: 130 }
                ]
            }]
    });

    //Render the initialized Spreadsheet control
    spreadsheet.appendTo('#spreadsheet');
```

{% endtab %}

> By default, `DataManager` uses **ODataAdaptor** for remote data-binding.

### Binding with OData services

`OData` is a standardized protocol for creating and consuming data. You can retrieve data from OData service using the DataManager. Refer to the following code example for remote Data binding using OData service.

{% tab template="spreadsheet/data-binding", sourceFiles="app.ts,index.html", es5Template="es5-oData", iframeHeight="450px" %}

```typescript

import { Spreadsheet } from '@syncfusion/ej2-spreadsheet';
import { DataManager, ODataAdaptor } from '@syncfusion/ej2-data';

//Initialize DataManager
let data: DataManager = new DataManager({
  url: 'https://ej2services.syncfusion.com/production/web-services/api/Orders',
  adaptor: new ODataAdaptor(),
  crossDomain: true
});
//Initialize Spreadsheet control
let spreadsheet: Spreadsheet = new Spreadsheet({
  sheets: [
    {
      name: 'Order details',
      ranges: [{ dataSource: data }],
      columns: [
        { width: 80 },
        { width: 80 },
        { width: 80 },
        { width: 80 },
        { width: 80 },
        { width: 80 },
        { width: 280 },
        { width: 180 },
        { width: 80 },
        { width: 180 },
        { width: 180 },
      ]
    }
  ],
  created: (): void => {
    //Applies cell and number formatting to specified range of the active sheet
    spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center', verticalAlign: 'middle' },
      'A1:K1');
  }
});

//Render the initialized Spreadsheet control
spreadsheet.appendTo('#spreadsheet');
```

{% endtab %}

### Web API

You can use WebApiAdaptor to bind spreadsheet with Web API created using OData endpoint.

{% tab template="spreadsheet/data-binding", sourceFiles="app.ts,index.html", es5Template="es5-webApi", iframeHeight="450px" %}

```typescript

import { Spreadsheet } from '@syncfusion/ej2-spreadsheet';
import { DataManager, WebApiAdaptor } from '@syncfusion/ej2-data';

//Initialize DataManager
let data: DataManager = new DataManager({
    url: 'https://ej2services.syncfusion.com/production/web-services/api/Orders',
    crossDomain: true,
    adaptor: new WebApiAdaptor()
});
//Initialize Spreadsheet control
let spreadsheet: Spreadsheet = new Spreadsheet({
  sheets: [
    {
      name: 'Order details',
      ranges: [{ dataSource: data }],
      columns: [
        { width: 80 },
        { width: 80 },
        { width: 80 },
        { width: 80 },
        { width: 80 },
        { width: 80 },
        { width: 280 },
        { width: 180 },
        { width: 80 },
        { width: 180 },
        { width: 180 },
      ]
    }
  ],
  created: (): void => {
    //Applies cell and number formatting to specified range of the active sheet
    spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center', verticalAlign: 'middle' },
      'A1:K1');
  }
});

//Render the initialized Spreadsheet control
spreadsheet.appendTo('#spreadsheet');
```

{% endtab %}

## Cell data binding

The Spreadsheet control can bind the data to individual cell in a sheet . To achive this you can use the
`value` property.

Refer to the following code example for cell data binding.

{% tab template="spreadsheet/data-binding", sourceFiles="app.ts,index.html" ,es5Template="es5-cell-data", iframeHeight="450px" %}

```typescript
import { Spreadsheet } from '@syncfusion/ej2-spreadsheet';

//Initialize the SpreadSheet control
let spreadsheet: Spreadsheet = new Spreadsheet({
    sheets: [
        {
            name: 'Monthly Budget',
            selectedRange: 'D13',
            rows: [
                {
                    cells: [
                        { value: 'Category', style: { fontWeight: 'bold', textAlign: 'center' } },
                        { value: 'Planned cost', style: { fontWeight: 'bold', textAlign: 'center' } },
                        { value: 'Actual cost', style: { fontWeight: 'bold', textAlign: 'center' } },
                        { value: 'Difference', style: { fontWeight: 'bold', textAlign: 'center' } }
                    ]
                },
                {
                    cells: [
                        { value: 'Food' },
                        { value: '$7000' },
                        { value: '$8120' },
                        { formula: '=B2-C2', format: '$#,##0.00' }
                    ]
                },
                {
                    cells: [
                        { value: 'Loan' },
                        { value: '$1500' },
                        { value: '$1500' },
                        { formula: '=B3-C3', format: '$#,##0.00' }
                    ]
                },
                {
                    cells: [
                        { value: 'Medical' },
                        { value: '$300' },
                        { value: '$0' },
                        { formula: '=B4-C4', format: '$#,##0.00' }
                    ]
                },
                {
                    index: 5,
                    cells: [
                        { index: 2, value: 'Total Difference:', style: { fontWeight: 'bold', textAlign: 'right' } },
                        { formula: '=D2+D4', format: '$#,##0.00', style: { fontWeight: 'bold' } }
                    ]
                }
            ],
            columns: [
                { width: 110 }, { width: 115 }, { width: 110 }, { width: 100 }
            ]
        }
    ]
});

//Render the initialized SpreadSheet
spreadsheet.appendTo('#spreadsheet');
```

{% endtab %}

> The cell data binding also supports formula, style, number format, and more.

## Dynamic data binding and Datasource change event

You can dynamically change the datasource of the spreadsheet by changing the `dataSource` property of the `range` object of the `sheet`. The `dataSourceChanged` event handler will be triggered when editing, inserting, and deleting a row in the datasource range. This event will be triggered with a parameter named `action` which indicates the `edit`, `add` and `delete` actions for the respective ones.

The following table defines the arguments of the `dataSourceChanged` event.

| Property | Type | Description |
|-----|-----|-------|
| action | string | Indicates the type of action such as `edit`, `add`, and `delete` performed in the datasource range. |
| data | object[] | Modified data for `edit` action; New data for `add` action; Deleted data for `delete` action. |
| rangeIndex | number | Specifies the range index of the datasource. |
| sheetIndex | number | Specifies the sheet index of the datasource. |

> For `add` action, the value for all the fields will be `null` in the data. In the case that you do not want the primary key field to be null which needs to be updated in the backend service, you can use `edit` action after updating the primary key field to update in the backend service. <br><br>
> For inserting a row at the end of the datasource range, you should insert a row below at the end of the range to trigger the `dataSourceChanged` event with action `add`.

{% tab template="spreadsheet/dynamic-data-binding", sourceFiles="app.ts,datasource.ts,index.html", es5Template="es5-dynamic-data-binding", iframeHeight="700px" %}

```typescript

import { Spreadsheet, DataSourceChangedEventArgs } from '@syncfusion/ej2-spreadsheet';
import { data, itemData } from './datasource.ts';

let spreadsheet: Spreadsheet = new Spreadsheet({
        showRibbon: false,
        showFormulaBar: false,
        sheets: [
            {
                ranges: [{ dataSource: data }],
                columns: [
                    { width: 90 }, { width: 100 }, { width: 96 },
                    { width: 120 }, { width: 130 }, { width: 120 }
                ]
            }],
        dataSourceChanged: (args: DataSourceChangedEventArgs) => {
            appendElement("Data source changed with" + "<b>&nbsp;" + args.action + "</b> action<hr>");
        }
});

spreadsheet.appendTo('#spreadsheet');

document.getElementById('changeDataBtn').addEventListener('click', ()=> {
    spreadsheet.sheets[0].ranges[0].dataSource = itemData;
});

document.getElementById('clearBtn').addEventListener('click', ()=> {
    document.getElementById('EventLog').innerHTML = "";
});

function appendElement(html: string): void {
     let span: HTMLElement = document.createElement("span");
     span.innerHTML = html;
     let log: HTMLElement = document.getElementById('EventLog');
     log.insertBefore(span, log.firstChild);
}

```

{% endtab %}

## See Also

* [Filtering](./filter)
* [Sorting](./sort)
* [Hyperlink](./link)
* [`Collaborative Editing`](use-cases/collaborative-editing)