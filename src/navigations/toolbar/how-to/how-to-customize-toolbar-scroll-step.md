---
title: "How to customize toolbar scrollStep"
component: "Toolbar"
description: "This example demonstrates how to customize the scrolling distance of Essential JS 2 Toolbar component items when clicking left or right navigation icons."
---

# How to customize toolbar scrollStep

Toolbar supports to customize the scrolling distance when you click the left and right side navigation icons. we can customize `ScrollStep` property for scrolling distance. Refer to the following code example.

* By using Toolbar scrollStep property, pass a required value to customize toolbar scrollStep.

{% tab template="toolbar/scrollstep", es5Template="es5_scrollstep", sourceFiles="index.ts,index.html,index.css" %}

```typescript

import { Toolbar, BeforeCreateArgs } from '@syncfusion/ej2-navigations';

let toolbarObj: Toolbar = new Toolbar({
        scrollStep: 50,
        width: 600,
        items: [
            {
                prefixIcon: 'e-cut-icon tb-icons', tooltipText: 'Cut' },
            {
                prefixIcon: 'e-copy-icon tb-icons', tooltipText: 'Copy' },
            {
                prefixIcon: 'e-paste-icon tb-icons', tooltipText: 'Paste' },
            {
                type: 'Separator' },
            {
                prefixIcon: 'e-bold-icon tb-icons', tooltipText: 'Bold' },
            {
                prefixIcon: 'e-underline-icon tb-icons', tooltipText: 'Underline' },
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

    function beforeCreate(e: BeforeCreateArgs) {
        e.scrollStep = 50;
    };

```

{% endtab %}