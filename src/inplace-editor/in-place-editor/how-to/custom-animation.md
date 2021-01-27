---
title: "Custom animation for popup mode"
component: "In-place Editor"
description: "Learn how to configure custom animation for popup and customize it dynamically in the Essential JS 2 In-place Editor control."
---

# Set custom animation for popup mode

In popup mode, the In-place Editor rendered with the Essential JS 2 `Tooltip` control. You can use tooltip properties and events to customize the popup by configure properties into the [model](../../api/inplace-editor/popupSettings/#model) property inside the [popupSettings](../../api/inplace-editor/popupSettings/) API.

In the following sample, popup animation can be customized by passing animation effect using the `model` property and the dynamic animation effect changes configured from the Essential JS 2 `DropDownList` control `change` event.

{% tab template="in-place-editor/custom-animation", es5Template="es5_custom_animation", sourceFiles="index.ts,index.html" %}

```typescript

import { InPlaceEditor } from '@syncfusion/ej2-inplace-editor';
import { DropDownList, ChangeEventArgs } from '@syncfusion/ej2-dropdowns';

var openAnimateData = ['None', 'FadeIn', 'FadeZoomIn', 'ZoomIn'];

let openDropObj: DropDownList = new DropDownList({
    value: 'ZoomIn',
    dataSource: openAnimateData,
    placeholder: 'Select a animate type',
    popupHeight: '150px',
    change: function(e: ChangeEventArgs): void {
        editObj.popupSettings.model.animation.open.effect = e.value;
        editObj.dataBind();
    }
});
openDropObj.appendTo('#openDropDown');

let editObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Popup',
    value: 'Andrew',
    model: {
        placeholder: 'Enter some text'
    },
    popupSettings: {
        model: {
            animation: {
                open: { effect: 'ZoomIn', duration: 1000, delay: 0 }
            }
        }
    }
});
editObj.appendTo('#element');

```

{% endtab %}