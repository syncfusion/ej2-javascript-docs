---
title: "Load content through Ajax"
component: "Accordion"
description: "This example demonstrates how to load the external content into the Essential JS 2 Accordion content through Ajax post."
---

# Load content through Ajax

Accordion supports to load external contents through `AJAX` library. Refer the below steps.

* Import the `Ajax` module from `ej2-base` and initialize with URL path.

* Get data from the Ajax Success event to initialize Accordion with retrieved external path data.

{% tab template="accordion/accordion-ajax", es5Template="es5_accordion_ajax", sourceFiles="index.ts,index.html,ajax.html" %}

```typescript
import {Accordion} from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';
import { Ajax } from '@syncfusion/ej2-base';

enableRipple(true);

let ajax: Ajax = new Ajax('./ajax.html', 'GET', true);
ajax.send().then();
ajax.onSuccess = (data: string): void => {
  let ctn2: string = data;
  let accordion: Accordion = new Accordion({
    items: [
      { header: 'Department', content: '#acrdnContent1' },
      { header: 'Platform', content: '#acrdnContent2' },
      { header: 'Employee Details', content: ctn2 }
    ]
 });
  accordion.appendTo('#element');
}

```

{% endtab %}