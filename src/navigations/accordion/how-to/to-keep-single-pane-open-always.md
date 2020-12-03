---
title: "To keep single pane open always"
component: "Accordion"
description: "This example demonstrates how to keep a single pane in an expanded state in the Essential JS 2 Accordion component."
---

# To keep single pane open always

By default, all Accordion panels are collapsible. You can customize the Accordion to keep one panel as expanded state always. This is applicable for `Single` expand mode.

{% tab template="accordion/accordion", es5Template="es5_accordion_keep_open", sourceFiles="index.ts,index.html"  %}

```typescript
import {Accordion, ExpandEventArgs, AccordionClickArgs} from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
let clickEle: HTMLElement;
let accordion: Accordion = new Accordion({
    expandMode: 'Single',
    clicked: clicked,
    expanding: beforeExpand,
    items: [
      { header: 'ASP.NET', expanded:'true', content: 'Microsoft ASP.NET is a set of technologies in the Microsoft .NET Framework for building Web applications and XML Web services.' },
      { header: 'ASP.NET MVC', content: 'The Model-View-Controller (MVC) architectural pattern separates an application into three main components: the model, the view, and the controller.' },
      { header: 'JavaScript', content: 'JavaScript (JS) is an interpreted computer programming language. It was originally implemented as part of web browsers so that client-side scripts could interact with the user, control the browser, communicate asynchronously, and alter the document content that was displayed.' },
    ]
});
accordion.appendTo('#element');

function clicked (e: AccordionClickArgs): void {
  clickEle = e.originalEvent.target;
}
function beforeExpand (e: ExpandEventArgs):void {
  let expandCount: number = this.element.querySelectorAll('.e-selected').length;
  let ele: HTMLElement= this.element.querySelectorAll('.e-selected')[0];
  if (ele) {
    ele = ele.firstChild
  }
  if (expandCount === 1 && ele === clickEle) {
    e.cancel = true;
  }
}
```

{% endtab %}
