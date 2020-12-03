---
title: "Add icon to Accordion header"
component: "Accordion"
description: "This example demonstrates how to add icons to the accordion header in the Essential JS 2 Accordion component."
---

# Add icon to Accordion header

You can add the icon custom css class to the Accordion header using ['iconCss'](../../api/accordion/accordionItem#iconcss) property and also add css styles to the defined class.  The accordion icon element is rendered before the header text in the DOM element.

{% tab template="accordion/accordion-icon", es5Template="es5_accordion_icon", sourceFiles="index.ts,index.html,datasource.ts" %}

```typescript
import { Accordion, ExpandEventArgs, AccordionClickArgs, AccordionItemModel } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';
import { accordion } from './datasource.ts';

enableRipple(true);

   //Initialize Accordion component
    let acrdnObj: Accordion = new Accordion({
        items: [
            { header: 'Athletics', iconCss: 'e-athletics e-acrdn-icons', content: '#athletics', expanded: true },
            { header: 'Water Games', iconCss: 'e-water-game e-acrdn-icons', content: '#water_games' },
            { header: 'Racing', iconCss: 'e-racing-games e-acrdn-icons', content: '#racing_games' },
            { header: 'Indoor Games', iconCss: 'e-indoor-games e-acrdn-icons', content: '#indoor_games' }
        ]
    });
    //Render initialized Accordion component
    acrdnObj.appendTo('#element');

```

{% endtab %}
