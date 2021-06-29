---
title: "Enable/Disable Toolbar Item"
component: "Toolbar"
description: "This example demonstrates how to enable/disable specific items in the Essential JS Toolbar."
---

# Enable/Disable Toolbar item

The [`disabled`](../../api/toolbar/itemModel/#disabled) property of the Toolbar item is used to enable/disable the item by setting false/true value to the property. In the following code example initially paste action will be disabled. On clicking the cut or copy button, the paste button will be enabled.

{% tab template="toolbar/scrollstep", es5Template="es5_disableitem", sourceFiles="index.ts,index.html,index.css" %}

```typescript

import { Toolbar } from '@syncfusion/ej2-navigations';

function onClick() {
  toolbarObj.items[2].disabled = false;
}
let toolbarObj: Toolbar = new Toolbar({
        width: 600,
        items: [
            {
                prefixIcon: 'e-cut-icon tb-icons', tooltipText: 'Cut', click: onClick},
            {
                prefixIcon: 'e-copy-icon tb-icons', tooltipText: 'Copy', click: onClick},
            {
                prefixIcon: 'e-paste-icon tb-icons', tooltipText: 'Paste', disabled: true },
            {
                type: 'Separator' },
            {
                prefixIcon: 'e-bold-icon tb-icons', tooltipText: 'Bold' },
            {
                prefixIcon: 'e-underline-icon tb-icons', tooltipText: 'Underline'},
            {
                prefixIcon: 'e-italic-icon tb-icons', tooltipText: 'Italic' },
            {
                prefixIcon: 'e-color-icon tb-icons', tooltipText: 'Color-Picker' },
            {
                type: 'Separator' },
            {
                prefixIcon: 'e-alignleft-icon tb-icons', tooltipText: 'Align-Left' },
            {
                prefixIcon: 'e-alignjustify-icon tb-icons', tooltipText: 'Align-Justify'},
            {
                prefixIcon: 'e-alignright-icon tb-icons', tooltipText: 'Align-Right' },
            {
                prefixIcon: 'e-aligncenter-icon tb-icons', tooltipText: 'Align-Center' },
            {
                type: 'Separator' },
            {
                prefixIcon: 'e-bullets-icon tb-icons', tooltipText: 'Bullets'},
            {
                prefixIcon: 'e-numbering-icon tb-icons', tooltipText: 'Numbering' },
            {
                type: 'Separator' },
            {
                prefixIcon: 'e-ascending-icon tb-icons', tooltipText: 'Sort A - Z' },
            {
                prefixIcon: 'e-descending-icon tb-icons', tooltipText: 'Sort Z - A' },
            {
                type: 'Separator' },
            {
                prefixIcon: 'e-upload-icon tb-icons', tooltipText: 'Upload' },
            {
                prefixIcon: 'e-download-icon tb-icons', tooltipText: 'Download' },
            {
                type: 'Separator' },
            {
                prefixIcon: 'e-indent-icon tb-icons', tooltipText: 'Text Indent' },
            {
                prefixIcon: 'e-outdent-icon tb-icons', tooltipText: 'Text Outdent' },
            {
                type: 'Separator' },
            {
                prefixIcon: 'e-clear-icon tb-icons', tooltipText: 'Clear' },
            {
                prefixIcon: 'e-reload-icon tb-icons', tooltipText: 'Reload' },
            {
                prefixIcon: 'e-export-icon tb-icons', tooltipText: 'Export'
            }]
    });
    toolbarObj.appendTo('#element');

```

{% endtab %}