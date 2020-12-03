---
title: "Set command customization"
component: "Toolbar"
description: "This example demonstrates how to set the HTML attribute commands to Essential JS 2 Toolbar component items."
---

# Set command customization

The [`htmlAttributes`](../../api/toolbar/item#htmlattributes) property of the Toolbar item is used to set the HTML attributes ('ID', 'class', 'style' ,'role') for the commands.

When style attributes are added, if the same attributes were already present, they will be replaced. This is not so in the case of `class` attribute. Classes will be added to the element instead of replacing the existing ones.

Single or multiple CSS classes can be added to the Toolbar commands using the Toolbar item [`cssClass`](../../api/toolbar/item#cssclass) property.

{% tab template="toolbar/toolbar-items", es5Template="es5_toolbar_custom", sourceFiles="index.ts,index.html" %}

```typescript

import {Toolbar} from '@syncfusion/ej2-navigations';
let toolbar: Toolbar = new Toolbar({
    width: 300,
    items: [
        { text: "Bold", type: 'Button', htmlAttributes: { 'class': 'custom_bold', 'id': 'itemId' } },
        { text: "Italic", htmlAttributes: { 'class': 'custom_italic' }  },
        { text: "Underline", htmlAttributes: { 'class': 'custom_underline' } },
        { type: "Separator" },
        { text: "Uppercase", cssClass: "e-txt-casing" }
    ]
});
toolbar.appendTo('#element');

```

{% endtab %}