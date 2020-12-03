---
title: "Load accordion with DataSource"
component: "Accordion"
description: "This example demonstrates how to bind any data object to accordion items in the Essential JS 2 Accordion component."
---

# Load accordion with DataSource

You can bind any data object to Accordion items, by mapping it to [`header`](../../api/accordion/accordionItem#header) and [`content`](../../api/accordion/accordionItem#content)&nbsp; property.

In the below demo, Data is fetched from an `OData` service using `DataManager`. The result data is formatted as a JSON object with `header` and `content` fields, which is set to items property of Accordion.

{% tab template="accordion/accordion", es5Template="es5_accordion_data", sourceFiles="index.ts,index.html" %}

```typescript

import { Accordion } from '@syncfusion/ej2-navigations';
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
      itemsData.push({ header: result[i][mapping.header], content: result[i][mapping.content] });
    }

    let accordion: Accordion = new Accordion({
      items: itemsData
    });
    accordion.appendTo('#element');
});

```

{% endtab %}
