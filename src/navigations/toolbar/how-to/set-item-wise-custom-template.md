---
title: "Set item-wise custom template"
component: "Toolbar"
description: "This example demonstrates how to create custom template into the Essential JS 2 Toolbar component items."
---

# Set item-wise custom template

The Toolbar supports adding template commands using the [`template`](../../api/toolbar/item#template) property. Template property can be given as the `HTML element` that is either a `string`  or a `query selector`.

## As a string

The HTML element tag can be given as a string for the template property. Here, the checkbox is rendered as a HTML template.

```typescript
template: "<div><input type='checkbox' id='check1' checked=''>Accept</input></div>"

```

## As a selector

The template property also allows getting template content through query `selector`. Here, checkbox 'ID' attribute is specified in the template.

```typescript
template: "#Template"

```

{% tab template="toolbar/toolbar-items-templateID", es5Template="es5_toolbar_templateID", sourceFiles="index.ts,index.html" %}

```typescript
import {Toolbar} from '@syncfusion/ej2-navigations';
let toolbar: Toolbar = new Toolbar({
    items: [
        { text: "Cut" },
        { type: "Separator" },
        { text: "Paste" },
        { type: "Separator" },
        { template: "<div><input type='checkbox' id='check1' checked=''>Accept</input></div>" },
        { text: "Undo" },
        { text: "Redo" },
        { template: "#Template" }
    ]
});
toolbar.appendTo('#element');
```

{% endtab %}