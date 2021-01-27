---
title: "Dynamically move input to edit mode"
component: "In-place Editor"
description: "Learn how to dynamically move input to edit mode in the Essential JS 2 In-place Editor control."
---

# Dynamically move input to edit mode

At control initial load, if you want to open editor state without interacting In-place Editor input element, it can be achieved by configuring the [enableEditMode](../../api/inplace-editor/#enableeditmode) property to `true`.

In the following sample, editor opened at initial load and when toggling a checkbox, it will remove or open the editor.

{% tab template="in-place-editor/dynamic-edit", es5Template="es5_dynamic_edit", sourceFiles="index.ts,index.html" %}

```typescript
import { InPlaceEditor, ActionBlur } from '@syncfusion/ej2-inplace-editor';
import { CheckBox, ChangeEventArgs } from '@syncfusion/ej2-buttons';

let CheckBoxObj: CheckBox = new CheckBox({ label: 'Enable', checked: true, change: onChange });
CheckBoxObj.appendTo('#enable');

let editObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    value: 'Andrew',
    enableEditMode: true,
    actionOnBlur: 'Ignore'
    model: {
        placeholder: 'Enter some text'
    }
});
editObj.appendTo('#element');

function onChange(e: ChangeEventArgs): void {
    editObj.enableEditMode = e.checked;
    editObj.dataBind();
}
```

{% endtab %}