---
title: "Custom indication for unsaved value"
component: "In-place Editor"
description: "Learn how to add a custom indication to the unsaved value of the Essential JS 2 In-place Editor control."
---

# Add custom indication to unsaved value

You can add custom indication to unsaved input value by using the [actionSuccess](../../api/inplace-editor/#actionsuccess) event, when data not submitted to the server.

In this sample, the `actionSuccess` event configured and the [URL](../../api/inplace-editor/#url) property not included. Then submit button clicked, the current editor value saved into input and data sending to server action prevented due to the `URL` property not configured.

But `actionSuccess` event will trigger the handler function with `null` argument values. In handler function data property [primaryKey](../../api/inplace-editor/#primarykey) value checked, whether it empty or not. If it is empty custom class, added in the `e-value-wrapper` element to customize its styles.

> To send input value to local, set the `URL` property as empty.

{% tab template="in-place-editor/custom-indication", es5Template="es5_custom_indication", sourceFiles="index.ts,index.html" %}

```typescript
import { isNullOrUndefined as isNOU } from '@syncfusion/ej2-base';
import { InPlaceEditor, ActionEventArgs } from '@syncfusion/ej2-inplace-editor';

let editObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    value: 'Andrew',
    model: {
        placeholder: 'Enter some text'
    },
    actionSuccess: function(e: ActionEventArgs): void {
        let pk: string = e.data['PrimaryKey'];
        if (isNOU(pk) || pk === '') {
            document.querySelector('.e-editable-value').classList.add('e-send-error');
        }
    }
});
editObj.appendTo('#element');
```

{% endtab %}