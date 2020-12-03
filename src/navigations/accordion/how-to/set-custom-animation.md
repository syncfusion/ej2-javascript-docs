---
title: "Set custom animation"
component: "Accordion"
description: "This example demonstrates how to set custom animation for expand and collapse actions in the Essential JS 2 Accordion component."
---

# Set custom animation

Accordion supports custom animations for both expand and collapse actions from the provided animation option of `Animation` library.  The [`animation`](../../api/accordion#animation) property also allows you to set [`easing`](../../api/accordion/accordionActionSettings#easing), [`duration`](../../api/accordion/accordionActionSettings#duration), and various other effects of your choice.

Default animation is given as `SlideDown` for expanding the panel using [`expand`](../../api/accordion/accordionAnimationSettings#expand) animation property and `SlideUp` for collapsing the panel using [`collapse`](../../api/accordion/accordionAnimationSettings#collapse) animation property. You can also disable the animation by setting animation [`effect`](../../api/accordion/accordionActionSettings#effect) as `none`.

The sample demonstrates some types of animation that suits for Accordion. You can check all the animation effects here.

{% tab template="accordion/accordion-custom-animation" , es5Template="es5_accordion_custom", sourceFiles="index.ts,index.html" %}

```typescript
import {Accordion, AccordionEffect} from '@syncfusion/ej2-navigations';
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let accordion: Accordion = new Accordion({
    items: [
      { header: 'ASP.NET', content: 'Microsoft ASP.NET is a set of technologies in the Microsoft .NET Framework for building Web applications and XML Web services.' },
      { header: 'ASP.NET MVC', content: 'The Model-View-Controller (MVC) architectural pattern separates an application into three main components: the model, the view, and the controller.' },
      { header: 'JavaScript', content: 'JavaScript (JS) is an interpreted computer programming language. It was originally implemented as part of web browsers so that client-side scripts could interact with the user, control the browser, communicate asynchronously, and alter the document content that was displayed.' },
    ]
});
accordion.appendTo('#element');
let listObjExpand: DropDownList = new DropDownList({
        index: 0,
        placeholder: 'Select a animate type',
        popupHeight: '150px',
        change: () => { valueChange();  }
    });
    listObjExpand.appendTo('#expandAnimation');
    valueChange();
let listObjCollapse: DropDownList = new DropDownList({
        index: 1,
        placeholder: 'Select a animate type',
        popupHeight: '150px',
        change: () => { valueChange1();  }
    });
    listObjCollapse.appendTo('#collapseAnimation');
    valueChange1();

function valueChange(): void {
  accordion.animation.expand.effect = <AccordionEffect>(listObjExpand.value);
  }
function valueChange1(): void {
  accordion.animation.collapse.effect = <AccordionEffect>(listObjCollapse.value);
  }
```

{% endtab %}
