---
title: "Integrate HTML5 controls"
component: "In-place Editor"
description: "Learn how to configure template and integrate HTML5 controls, get and pass a modified value to the server in the Essential JS 2 In-place Editor control."
---

# Integrate HTML5 controls (Template)

The In-place Editor supports adding HTML5 input controls using the [template](../api/inplace-editor/#template) property. The Template property can be given as either a `string` or a `query selector`.

## As a string

The HTML element tag can be given as a string for the template property. Here, the input is rendered as an HTML template.

```typescript
template: "<div><input type='text' id='name'></input></div>"

```

## As a selector

The template property also allows getting template content through query `selector`. Here, the input wrapper element 'ID' attribute is specified in the template.

```typescript
template: "#date"

```

Template mode, the `value` property not handled by the In-place Editor control. So, before sending a value to the server, you need to modify at [actionBegin](../api/inplace-editor/#actionbegin) event, otherwise, an empty string will pass. In the following template sample, before submitting a data to the server, event argument and [value](../api/inplace-editor/#value) property content updated in the `actionBegin` event handler.

{% tab template="in-place-editor/html-template", es5Template="es5_html_template", sourceFiles="index.ts,index.html" %}

```typescript
import { InPlaceEditor, ActionBeginEventArgs } from '@syncfusion/ej2-inplace-editor';

let editObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    template: '#date',
    value: '2018-05-23',
    actionBegin: function(e: ActionBeginEventArgs): void {
        let value: string = (<HTMLInputElement>editObj.element.querySelector('#date')).value;
        editObj.value = value;
        e.value = value;
    }
});
editObj.appendTo('#element');
```

{% endtab %}

## See Also

* [Built-in Controls](./controls/)