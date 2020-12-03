---
title: "Load accordion items dynamically"
component: "Accordion"
description: "This example demonstrates how to dynamically load or add an accordion item in the Essential JS 2 Accordion component."
---

# Load accordion items dynamically

Accordion items can be added dynamically by passing the item and index value with the [`addItem`](../../api/accordion#additem) method.

In the following demo, new items are added dynamically when you expand an Accordion header using [`expanded`](../../api/accordion#expanded) event.

* Data is fetched from the data source and it is formatted as a JSON object with `header` and `content` fields.

* Here last index is calculated to append the new Accordion item at the end and the number of items are limited to 10, since the data bound have only 10 items.

{% tab template="accordion/accordion-items-dynamically", es5Template="es5_accordion_items_dynamically", sourceFiles="index.ts,index.html,datasource.ts" %}

```typescript
import { Accordion, ExpandEventArgs, AccordionClickArgs, AccordionItemModel } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';
import { accordion } from './datasource.ts';

enableRipple(true);

    let dbFlag: number = 0;
    let dynamciAcrdnCount: number = 2;
    let acrdnObj: Accordion = new Accordion({
       expanded: expanded,
       items : [
           { header: 'ASP.NET', content: 'Microsoft ASP.NET is a set of technologies in the Microsoft .NET Framework for building Web applications and XML Web services.' },
           { header:  ' ASP.NET Core ', content: ' ASP.NET Core is a free and open-source web framework, and the next generation of ASP.NET, developed by Microsoft and the community. It is a modular framework that runs on both the full .NET Framework, on Windows, and the cross-platform .NET Core.' },
           { header: 'ASP.NET MVC', content : 'The Model-View-Controller (MVC) architectural pattern separates an application into three main components: the model, the view, and the controller.' },
       ]
    });
    acrdnObj.appendTo('#Accordion_default');
    function expanded( e: ExpandEventArgs) {
        //Find the expanded state item in accordion
        let Elementindex = document.getElementsByClassName("e-expand-state e-selected e-active")[0];
        //Check the expand state item and currently selected item index. If it is expanded state add dyanmic items or else does nothing
        if([].slice.call(e.element.parentElement.children).indexOf(e.element) == [].slice.call(e.element.parentElement.children).indexOf(Elementindex)) {
          let array: AccordionItemModel[] = accordion as AccordionItemModel[];
          for(let i: number = 0 ; i < dynamciAcrdnCount; i++)
          {
            if (dbFlag === array.length) { //checking whether all the items in data source added
                return; }
            // Item object and the index argument passed into the additem method to add a new accordion
            acrdnObj.addItem( array[dbFlag] , acrdnObj.items.length );
            ++dbFlag;
          }
        }
    }

```

{% endtab %}
