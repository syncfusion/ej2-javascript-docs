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
                prefixIcon: 'e-cut-icon', tooltipText: 'Cut' },
            {
                prefixIcon: 'e-copy-icon', tooltipText: 'Copy' },
            {
                prefixIcon: 'e-paste-icon', tooltipText: 'Paste' },
            {
                type: 'Separator' },
            {
                prefixIcon: 'e-bold-icon', tooltipText: 'Bold' },
            {
                prefixIcon: 'e-underline-icon', tooltipText: 'Underline' },
            {
                prefixIcon: 'e-italic-icon', tooltipText: 'Italic' },
            {
                prefixIcon: 'e-color-icon', tooltipText: 'Color-Picker' },
            {
                type: 'Separator' },
            {
                prefixIcon: 'e-alignleft-icon', tooltipText: 'Align-Left' },
            {
                prefixIcon: 'e-alignjustify-icon', tooltipText: 'Align-Justify'},
            {
                prefixIcon: 'e-alignright-icon', tooltipText: 'Align-Right' },
            {
                prefixIcon: 'e-aligncenter-icon', tooltipText: 'Align-Center' },
            {
                type: 'Separator' },
            {
                prefixIcon: 'e-bullets-icon', tooltipText: 'Bullets'},
            {
                prefixIcon: 'e-numbering-icon', tooltipText: 'Numbering' },
            {
                type: 'Separator' },
            {
                prefixIcon: 'e-ascending-icon', tooltipText: 'Sort A - Z' },
            {
                prefixIcon: 'e-descending-icon', tooltipText: 'Sort Z - A' },
            {
                type: 'Separator' },
            {
                prefixIcon: 'e-upload-icon', tooltipText: 'Upload' },
            {
                prefixIcon: 'e-download-icon', tooltipText: 'Download' },
            {
                type: 'Separator' },
            {
                prefixIcon: 'e-indent-icon', tooltipText: 'Text Indent' },
            {
                prefixIcon: 'e-outdent-icon', tooltipText: 'Text Outdent' },
            {
                type: 'Separator' },
            {
                prefixIcon: 'e-clear-icon', tooltipText: 'Clear' },
            {
                prefixIcon: 'e-reload-icon', tooltipText: 'Reload' },
            {
                prefixIcon: 'e-export-icon', tooltipText: 'Export'
            }]
    });
    toolbarObj.appendTo('#element');

    function beforeCreate(e: BeforeCreateArgs) {
        e.scrollStep = 50;
    };

```

{% endtab %}