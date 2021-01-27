---
title: "Configuration"
component: "In-place Editor"
description: "Learn how to configure various renders, display modes, and configure the focus out actions in the Essential JS 2 In-place Editor control."
---

# Configuration

## Rendering modes

This section explains the supported rendering modes of the In-place Editor. Possible Rendering modes are as follows.

    * Popup
    * Inline

> By default, `Popup` mode will be rendered, when opening an editor.

* For `Popup` mode, editable container displays as like tooltip or popover above the element.

* For `Inline` mode, editable container displays as instead of the element. To render `Inline` mode while opening the editor, specify `mode` as `Inline`.

In the following sample, the In-place Editor renders with `Inline` mode. You can dynamically switch into another mode by changing the drop-down item value.

{% tab template="in-place-editor/modes", es5Template="es5_modes", sourceFiles="index.ts,index.html" %}

```typescript
import { InPlaceEditor, RenderMode } from '@syncfusion/ej2-inplace-editor';
import { DropDownList, ChangeEventArgs } from '@syncfusion/ej2-dropdowns';

let modeData: string[] = ['Inline', 'Popup'];

let modeObj: DropDownList = new DropDownList({
    dataSource: modeData,
    width: 'auto',
    change: onChange,
    value: 'Inline',
    placeholder: 'Select Mode'
});
modeObj.appendTo('#dropDown');

let editObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    value: 'Andrew',
    model: {
        placeholder: 'Enter some text'
    }
});
editObj.appendTo('#element');

function onChange(e: ChangeEventArgs): void {
    let mode: RenderMode = e.itemData.value as RenderMode;
    /* Switch into another mode */
    editObj.mode = mode;
    editObj.dataBind();
}
```

{% endtab %}

### Pop-up customization

In-place Editor popup mode can be customized by using the [title](../api/inplace-editor/popupSettings/#title) and [model](../api/inplace-editor/popupSettings/#model) properties in [popupSettings](../api/inplace-editor/popupSettings/) API.

Popup mode rendered by using the Essential JS 2 Tooltip control, so you can use tooltip properties and events to customize the behavior of popup via the [model](../api/inplace-editor/popupSettings/#model) property of [popupSettings](../api/inplace-editor/popupSettings/) API.

> For more details, refer the tooltip documentation [section](../tooltip/).

In the following sample, popup [title](../api/inplace-editor/popupSettings/#title) and [position](../api/tooltip/#position) customized using the [popupSettings](../api/inplace-editor/popupSettings/) property. All possible tooltip position data configured in the drop-down, if we change drop down item, selected value bound to [model](../api/inplace-editor/popupSettings/#model) property and applied it to [Tooltip](../tooltip/) control. `Tooltip` have following position options.

* TopLeft
* TopCenter
* TopRight
* BottomLeft
* BottomCenter
* BottomRight
* LeftTop
* LeftCenter
* LeftBottom
* RightTop
* RightCenter
* RightBottom

{% tab template="in-place-editor/popup", es5Template="es5_popup_customize", sourceFiles="index.ts,index.html" %}

```typescript
import { InPlaceEditor } from '@syncfusion/ej2-inplace-editor';
import { DropDownList, ChangeEventArgs } from '@syncfusion/ej2-dropdowns';

let positionData: string[] = ['TopLeft', 'TopCenter', 'TopRight', 'BottomLeft', 'BottomCenter', 'BottomRight', 'LeftTop', 'LeftCenter', 'LeftBottom', 'RightTop', 'RightCenter', 'RightBottom'];

let dropDownObj: DropDownList = new DropDownList({
    value: 'BottomCenter',
    dataSource: positionData,
    placeholder: 'Select a position',
    popupHeight: '150px',
    change: function(e: ChangeEventArgs): void {
        editObj.popupSettings.model.position = e.value;
        editObj.dataBind();
    }
});
dropDownObj.appendTo('#dropDown');

let editObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Popup',
    value: 'Andrew',
    model: {
        placeholder: 'Enter some text'
    },
    popupSettings: {
        title: 'Enter name',
        model: {
            position: 'BottomCenter'
        }
    }
});
editObj.appendTo('#element');
```

{% endtab %}

## Event actions for editing

The event action of the editor that enable in the edit mode based on the [editableOn](../api/inplace-editor/#editableon) property, by default `Click` is assigned, the following options are also supported.

* **[Click](../api/inplace-editor/editableType/)**:  The editor will be opened as single click actions.
* **[DblClick](../api/inplace-editor/editableType/)**: The editor will be opened as double-click actions and it is not applicable for edit icon.
* **[EditIconClick](../api/inplace-editor/editableType/)**: Disables the editing of event action of input and allows user to edit only through edit icon.

> In-place Editor get focus by pressing the `tab` key from previous focusable DOM element and then by pressing `enter` key, the editor will be opened.

In the following sample, when switching drop-down item, the selected value assigned to the `editableOn` property. If you changed to `DblClick`, the editor will open when making a double click on the input.

{% tab template="in-place-editor/editable-on", es5Template="es5_editable_on", sourceFiles="index.ts,index.html" %}

```typescript
import { InPlaceEditor, EditableType } from '@syncfusion/ej2-inplace-editor';
import { DropDownList, ChangeEventArgs } from '@syncfusion/ej2-dropdowns';

let editableOnData: string[] = ['Click', 'DblClick', 'EditIconClick'];

let dropDownObj: DropDownList = new DropDownList({
    dataSource: editableOnData,
    width: 'auto',
    value: 'Click',
    change: onChange,
    placeholder: 'Select edit type'
});
dropDownObj.appendTo('#dropDown');

let editObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    value: 'Andrew',
    model: {
        placeholder: 'Enter some text'
    }
});
editObj.appendTo('#element');

function onChange(e: ChangeEventArgs): void {
    let editType: EditableType = e.itemData.value as EditableType;
    editObj.editableOn = editType;
    editObj.dataBind();
}
```

{% endtab %}

## Action on focus out

Action to be performed when the user clicks outside the container, that means focusing out of editable content and it can be handled by the [actionOnBlur](../api/inplace-editor/#actiononblur) property, by default `Submit` assigned. It also has the following options.

* **[Cancel](../api/inplace-editor/actionBlur/)**: Cancels the editing and resets the old content.
* **[Submit](../api/inplace-editor/actionBlur/)**: Submits the edited content to the server.
* **[Ignore](../api/inplace-editor/actionBlur/)**: No action is performed with this type and allows to edit multiple editors.

In the following sample, when switching drop-down item, the selected value assigned to the `actionOnBlur` property.

{% tab template="in-place-editor/action-on-blur", es5Template="es5_action_on_blur", sourceFiles="index.ts,index.html" %}

```typescript
import { InPlaceEditor, ActionBlur } from '@syncfusion/ej2-inplace-editor';
import { DropDownList, ChangeEventArgs } from '@syncfusion/ej2-dropdowns';

let blurActionData: string[] = ['Submit', 'Cancel', 'Ignore'];

let dropDownObj: DropDownList = new DropDownList({
    dataSource: blurActionData,
    width: 'auto',
    value: 'Submit',
    change: onChange,
    placeholder: 'Select blur action'
});
dropDownObj.appendTo('#dropDown')

let editObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    value: 'Andrew',
    model: {
        placeholder: 'Enter some text'
    }
});
editObj.appendTo('#element');

function onChange(e: ChangeEventArgs): void {
    let editType: ActionBlur = e.itemData.value as ActionBlur;
    editObj.actionOnBlur = editType;
    editObj.dataBind();
}
```

{% endtab %}

## Display modes

By default, In-place Editor input element highlighted with a dotted underline. To remove dotted underline from input element, add `data-underline="false"` attribute at In-place Editor root element.

In the following sample, denotes to indicate intractable and normal display modes with different samples.

{% tab template="in-place-editor/under-line", es5Template="es5_under_line", sourceFiles="index.ts,index.html" %}

```typescript
import { InPlaceEditor, ActionBlur } from '@syncfusion/ej2-inplace-editor';

let defaultObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    value: 'Andrew',
    model: {
        placeholder: 'Enter some text'
    }
});
defaultObj.appendTo('#default');

let inlineObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    value: 'Andrew',
    model: {
        placeholder: 'Enter some text'
    }
});
inlineObj.appendTo('#inline');
```

{% endtab %}

## See Also

* [Disable the editor](./how-to/disable-edit-mode)
* [Animate the editor during popup mode](./how-to/custom-animation)