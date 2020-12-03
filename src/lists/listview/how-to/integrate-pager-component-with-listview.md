---
title: "ListView how to integrate pager component with listview"
component: "ListView"
description: "ListView how to section, with pagination support."
---

# How to integrate pager component with listview

The first and foremost step is to obtain the `Pager` component from `Grid`. Install the ej2-grid package using the following command.

```shell
npm install @syncfusion/ej2-grids --save
```

Import the Pager to the ListView sample which has been created.

```shell
import { Pager } from "@syncfusion/ej2-grids";
```

The [`totalRecordsCount`](https://ej2.syncfusion.com/documentation/api/pager/#totalrecordscount) property of Pager must be specified whenever using this particular component. By using [`pageSize`](https://ej2.syncfusion.com/documentation/api/pager/#pagesize) property, the number of list items to be displayed is made available. The [`pageCount`](https://ej2.syncfusion.com/documentation/api/pager/#pagecount) property allows the user to specify the visibility of the page numbers accordingly. Since the paging sample in the upcoming code snippet uses these three properties, the explanation provided here were minimal and to the point. For further API concerns in Pager component, [click here](https://ej2.syncfusion.com/documentation/api/pager/).

With the help of the `query` property of ListView, the user can specify the number of records to be displayed in the current page.

The [`query`](../../api/list-view#query) property helps in splitting the entire datasource based on our convenience. In the sample provided below, when clicking the next button in pager, it fetches the datasource based on page size and current page of Pager component.

```typescript
 click: function () {
        listObj.query= new Query().range((pager.currentPage - 1) * pager.pageSize, (pager.currentPage * pager.pageSize));
    }
```

Note: When `pageSize` isn't mentioned, it defaults to 12 records per page.

{% tab template="listview/paging", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css", es5Template="page-template" %}

```typescript

import { ListView } from '@syncfusion/ej2-lists';
import { Pager } from "@syncfusion/ej2-grids";
import { DataManager, Query, JsonAdaptor } from '@syncfusion/ej2-data';
import { data } from './datasource.ts';
let pager: Pager = new Pager({
    totalRecordsCount: data.length,
    pageSize: 10,
    pageCount:2,
    click: function () {
        listObj.query= new Query().range((pager.currentPage - 1) * pager.pageSize, (pager.currentPage * pager.pageSize));
    }
});
pager.appendTo('#Pager');
let header: string = '<table class="w-100"> <tr><td class="w-25">Order ID</td><td class="w-45">Ship Name</td><td class="w-25">ShipCity</td></tr></table>';
let template: string = '<table class="w-100"> <colgroup><col span="2"><col></colgroup><tr><td class="w-25">${OrderID}</td><td class="w-45">${ShipName}</td><td class="w-25">${ShipCity}</td></tr></table>';
//Initialize ListView component
// Initialize the ListView control
let listObj: ListView = new ListView({
 //Set the defined data to the data source property
    dataSource: new DataManager({
    json: data,
    adaptor: new JsonAdaptor
}),
query:new Query().range(0, pager.pageSize),
template:template,
headerTemplate:header,
showHeader:true
});
//Render the initialized ListView control
listObj.appendTo('#element');

```

{% endtab %}
