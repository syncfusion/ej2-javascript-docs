---
title: "Disable the edit mode specifically"
component: "In-place Editor"
description: "Learn how to disable the edit mode in the Essential JS 2 In-place Editor control."
---

# Disable the edit mode specifically

The edit mode of In-place Editor can be disabled by setting the [disabled](../../api/inplace-editor/#disabled) property value to `true`. In the following sample, when check or uncheck the checkbox, In-place Editor control will disable or enable the edit mode.

{% tab template="in-place-editor/disable-edit", es5Template="es5_disable_edit", sourceFiles="index.ts,index.html" %}

```typescript
import { InPlaceEditor } from '@syncfusion/ej2-inplace-editor';
import { CheckBox, ChangeEventArgs } from '@syncfusion/ej2-buttons';

let CheckBoxObj: CheckBox = new CheckBox({ label: 'Disable', checked: false, change: onChange });
CheckBoxObj.appendTo('#enable');

let editObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    value: 'Andrew',
    model: {
        placeholder: 'Enter some text'
    }
});
editObj.appendTo('#element');

function onChange(e: ChangeEventArgs): void {
    editObj.disabled = e.checked;
    editObj.dataBind();
}
```

{% endtab %}