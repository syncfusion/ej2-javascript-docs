---
title: "Load tab with DataSource"
component: "Tab"
description: "This example demonstrates how to bind any data object to tab Items in the Essential JS 2 Tab component."
---

# Load tab with DataSource

You can bind any data object to Tab items, by mapping it to a [`header`](../../api/tab/tabItem#header) and [`content`](../../api/tab/tabItem#content)&nbsp; property.

In the below demo, Data is fetched from an `OData` service using `DataManager`. The result data is formatted as a JSON object with `header` and `content` fields, which is set to items property of Tab.

{% tab template="tab/tab", es5Template="es5_data_tab", sourceFiles="index.ts,index.html" %}

```typescript

import { Tab } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';
import { DataManager, Query, ODataAdaptor, ReturnOption } from '@syncfusion/ej2-data';

enableRipple(true);

let itemsData: any = [];
let mapping =  { header: 'FirstName', content: 'Notes' };
const SERVICE_URI: string = 'https://js.syncfusion.com/ejServices/Wcf/Northwind.svc/Employees';

new DataManager({ url: SERVICE_URI, adaptor: new ODataAdaptor})
  .executeQuery(new Query().range(1, 4)).then((e: ReturnOption) => {
    let result: any = e.result;

    for(let i: number = 0; i < result.length; i++) {
      itemsData.push({ header: {text: result[i][mapping.header]}, content: result[i][mapping.content] });
    }

    let tabObj: Tab = new Tab({
      items: itemsData
    });
    tabObj.appendTo('#element');
});

```

{% endtab %}
