---
title: "Accordion Expand mode"
component: "Accordion"
description: "The Accordion component supports expand mode options, that specify the types of expand mode while expanding or collapsing an item."
---

# ExpandMode

 The Accordion supports the two listed types of expand modes while expanding or collapsing the item.

* Single
* Multiple

## Single

The property enables to expand only one Accordion item at a time. If you expand any new item, the previously expanded one is collapsed and new item changed to expanded state.

You can also choose which accordion pane is expanded state at initial rendering by enabling the [`expanded`](../api/accordion/accordionItemModel#expanded) property on accordion items.

{% tab template="accordion/accordion", es5Template="es5_accordion_single", sourceFiles="index.ts,index.html"%}

```typescript
import {Accordion} from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
let accordion: Accordion = new Accordion({
    expandMode: 'Single',
    items: [
      { header: 'ASP.NET', expanded: true, content: 'Microsoft ASP.NET is a set of technologies in the Microsoft .NET Framework for building Web applications and XML Web services.' },
      { header: 'ASP.NET MVC', content: 'The Model-View-Controller (MVC) architectural pattern separates an application into three main components: the model, the view, and the controller.' },
      { header: 'JavaScript', content: 'JavaScript (JS) is an interpreted computer programming language. It was originally implemented as part of web browsers so that client-side scripts could interact with the user, control the browser, communicate asynchronously, and alter the document content that was displayed.' },
    ]
});
accordion.appendTo('#element');
```

{% endtab %}

## Multiple

Default [`expandMode`](../api/accordion#expandmode) of the Accordion is `Multiple`. It enables you to expand more than one Accordion item at a time. Expand/collapse action can also be toggled by clicking on it again. For example, expanded item is collapsed when you click on it again.

{% tab template="accordion/accordion", es5Template="es5_accordion_multiple", sourceFiles="index.ts,index.html"%}

```typescript
import {Accordion} from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);
let accordion: Accordion = new Accordion({
    expandMode: 'Multiple',
    items: [
      { header: 'ASP.NET', content: 'Microsoft ASP.NET is a set of technologies in the Microsoft .NET Framework for building Web applications and XML Web services.' },
      { header: 'ASP.NET MVC', content: 'The Model-View-Controller (MVC) architectural pattern separates an application into three main components: the model, the view, and the controller.' },
      { header: 'JavaScript', content: 'JavaScript (JS) is an interpreted computer programming language. It was originally implemented as part of web browsers so that client-side scripts could interact with the user, control the browser, communicate asynchronously, and alter the document content that was displayed.' },
    ]
});
accordion.appendTo('#element');
```

{% endtab %}

## See Also

* [How to keep single pane open always](./how-to/to-keep-single-pane-open-always)