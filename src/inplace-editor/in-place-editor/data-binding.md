---
title: "Data Binding"
component: "In-place Editor"
description: "Learn how to bind local and remote data for dependent controls of the Essential JS 2 In-place Editor control."
---

# Data Binding

The Essential JS 2 controls load the data either from local data sources or remote data services using the `dataSource` property and it supports the data type of an array or `DataManager`. Also supports different kind of data services such as OData, OData V4, Web API, and data formats such as XML, JSON, JSONP with the help of `DataManager` adaptors.

## Local

To bind local data to the Essential JS 2 controls, you can assign a JavaScript array of object or string to the `dataSource` property. The local data source can also be provided as an instance of the `DataManager`.

{% tab template="in-place-editor/data", es5Template="es5_local_data", sourceFiles="index.ts,index.html" %}

```typescript
import { InPlaceEditor } from '@syncfusion/ej2-inplace-editor';

let gameList: { [key: string]: Object }[] = [
    { Id: '1', Name: 'Maria Anders' },
    { Id: '2', Name: 'Ana Trujillo' },
    { Id: '3', Name: 'Antonio Moreno' },
    { Id: '4', Name: 'Thomas Hardy' },
    { Id: '5', Name: 'Chiristina Berglund' },
    { Id: '6', Name: 'Hanna Moos' }
];

let editObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    type: 'DropDownList',
    value: 'Maria Anders',
    model: {
        dataSource: gameList,
        fields: { text: 'Name' },
        placeholder: 'Select a customer'
    }
});
editObj.appendTo('#element');
```

{% endtab %}

## Remote

To bind remote data to the Essential JS 2 control, assign service data as an instance of `DataManager` to the `dataSource` property. To interact with remote data source, provide the endpoint URL.

### OData V4

The OData V4 is an improved version of OData protocols, and the [DataManager](../data/getting-started/) can also retrieve and consume OData V4 services. To fetch data from the server by using `DataManager` with the adaptor property configure as [ODataV4Adaptor](../data/adaptors/#odatav4-adaptor).

In the following sample, In-place Editor renders a `DropDownList` control and its `dataSource` property configured for fetching a data from the server by using `ODataV4Adaptor` with `DataManager`.

{% tab template="in-place-editor/data", es5Template="es5_odata", sourceFiles="index.ts,index.html" %}

```typescript
import { DataManager, ODataV4Adaptor, Query } from '@syncfusion/ej2-data';
import { InPlaceEditor } from '@syncfusion/ej2-inplace-editor';

let editObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    type: 'DropDownList',
    value: 'Maria Anders',
    model: {
        dataSource: new DataManager({
            url: 'https://services.odata.org/V4/Northwind/Northwind.svc/',
            adaptor: new ODataV4Adaptor,
            crossDomain: true
        }),
        placeholder:"Select a customer",
        query: new Query().from('Customers').select(['ContactName', 'CustomerID']).take(6),
        fields: { text: 'ContactName', value: 'CustomerID' }
    }
});
editObj.appendTo('#element');
```

{% endtab %}

### Web API

Data can fetch from the server by using [DataManager](../data/getting-started/) with the adaptor property configure as [WebApiAdaptor](../data/adaptors/#web-api-adaptor).

In the following sample, In-place Editor render a `DropDownList` control and its `dataSource` property configured for fetching a data from the server by using `WebApiAdaptor` with `DataManager`.

{% tab template="in-place-editor/data", es5Template="es5_webapi", sourceFiles="index.ts,index.html" %}

```typescript
import { DataManager, WebApiAdaptor, Query } from '@syncfusion/ej2-data';
import { InPlaceEditor } from '@syncfusion/ej2-inplace-editor';

new DataManager({
    url: 'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Customers/',
    adaptor: new WebApiAdaptor
}).executeQuery(new Query().take(8)).then((e: any) => {
    let editObj: InPlaceEditor = new InPlaceEditor({
        mode: 'Inline',
        type: 'DropDownList',
        value: 'Maria Anders',
        model: {
            dataSource: e.result.d,
            placeholder:"Select a customer",
            fields: { text: 'ContactName', value: 'CustomerID' }
        }
    });
    editObj.appendTo('#element');
});
```

{% endtab %}