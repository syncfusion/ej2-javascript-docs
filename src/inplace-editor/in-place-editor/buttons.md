---
title: "Buttons"
component: "In-place Editor"
description: "Learn how to show or hide buttons, customize its behavior, and the appearance in the Essential JS 2 In-place Editor control."
---

# Buttons

The In-place Editor had an action for save and cancel using buttons. The [saveButton](../api/inplace-editor/#savebutton) and [cancelButton](../api/inplace-editor/#cancelbutton) properties accept the [ButtonModel](../api/button/buttonModel/) objects for customizing the save and cancel button properties.

Buttons can be show or hide by sets a Boolean value to the [showButtons](../api/inplace-editor/#showbuttons) property.

> Without buttons value will be processed via the following ways.

* **[actionOnBlur](../api/inplace-editor/#actiononblur)**: By clicking out side the editor control get focus out and do action based on this property value.
* **[submitOnEnter](../api/inplace-editor/#submitonenter)**: Pressing `Enter` key it performs the submit action, if this property set to `true`.

In the following sample, the [content](../api/button#content) and [cssClass](../api/button#cssclass) properties of `Button` value assigned to the [saveButton](../api/inplace-editor/#savebutton) and [cancelButton](../api/inplace-editor/#cancelbutton) properties to customize its appearance. Also check or uncheck a checkbox buttons render or removed from the editor.

To restrict either save or cancel button rendering into a DOM, simply pass empty object `{}` in the  `saveButton` or `cancelButton` properties.

> For more details about buttons, refer this documentation [section](../button/).

{% tab template="in-place-editor/show-buttons", es5Template="es5_show_buttons", sourceFiles="index.ts,index.html" %}

```typescript
import { InPlaceEditor, ActionBlur } from '@syncfusion/ej2-inplace-editor';
import { CheckBox, ChangeEventArgs } from '@syncfusion/ej2-buttons';

let CheckBoxObj: CheckBox = new CheckBox({ label: 'Show', checked: true, change: onChange });
CheckBoxObj.appendTo('#enableBtn');

let editObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    value: 'Andrew',
    model: {
        placeholder: 'Enter some text'
    },
    saveButton: {
        content: 'Ok',
        cssClass: 'e-outline'
    },
    cancelButton: {
        content: 'Cancel',
        cssClass: 'e-outline'
    }
});
editObj.appendTo('#element');

function onChange(e: ChangeEventArgs): void {
    editObj.showButtons = e.checked;
    editObj.dataBind();
}
```

{% endtab %}

## See Also

* [In-place Editor buttons](./how-to/dynamic-edit-mode)