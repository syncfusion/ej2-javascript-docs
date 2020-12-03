---
title: "Add Toggle Button"
component: "Toolbar"
description: "This example demonstrates how to add the Essential JS 2 Toggle Button into Essential JS Toolbar items."
---

# Add Toggle Button

Toolbar supports to add a toggle Button by using the template property. Refer below steps

* By using Toolbar template property, pass required HTML String to render toggle button.

```typescript
    { template: '<button class="e-btn" id="media_btn"></button>' }
```

* Now render the toggle Button into the targeted element in Toolbar [`created`](../../api/toolbar#created) event handler and bind click event for it. On clicking the toggle Button, change the required icon and content based on current active state.

{% tab template="toolbar/toggle-button", es5Template="es5_toggle_button", sourceFiles="index.ts,index.html,index.css" %}

```typescript

import { Button  } from '@syncfusion/ej2-buttons';
import { Toolbar } from '@syncfusion/ej2-navigations';

let undoBtn: any;
let zoomBtn: any;
let mediaBtn: any;
let filterBtn: any;
let visibleBtn: any;

let toolbar: Toolbar = new Toolbar({
    created: create,
    items: [
        { template: '<button class="e-btn" id="media_btn"></button>' },
        { type: "Separator" },
        { template: '<button class="e-btn" id="zoom_btn"></button>' },
        { type: "Separator" },
        { template: '<button class="e-btn" id="undo_btn"></button>' },
        { type: "Separator" },
        { template: '<button class="e-btn" id="filter_btn"></button>' },
        { type: "Separator" },
        { template: '<button class="e-btn" id="visible_btn"></button>'},
    ]
});
toolbar.appendTo('#element');

function create() {
    zoomBtn = new Button({ cssClass: `e-flat`, iconCss: 'e-icons e-zoomin-icon', isToggle: true });
    zoomBtn.appendTo('#zoom_btn');

    mediaBtn = new Button({ cssClass: `e-flat`, iconCss: 'e-icons e-play-icon', isToggle: true });
    mediaBtn.appendTo('#media_btn');

    undoBtn = new Button({ cssClass: `e-flat`, iconCss: 'e-icons e-undo-icon', isToggle: true });
    undoBtn.appendTo('#undo_btn');

    filterBtn = new Button({ cssClass: `e-flat`, iconCss: 'e-icons e-filter-icon', isToggle: true });
    filterBtn.appendTo('#filter_btn');

    visibleBtn = new Button({ cssClass: `e-flat`, iconCss: 'e-icons e-hide-icon', isToggle: true, content:'Hide'});
    visibleBtn.appendTo('#visible_btn');

    //Toggle button click event handlers
    zoomBtn.element.onclick = (): void => {
        if (zoomBtn.element.classList.contains('e-active')) {
            zoomBtn.iconCss = 'e-icons e-zoomout-icon';
        } else {
            zoomBtn.iconCss = 'e-icons e-zoomin-icon';
        }
    };

    mediaBtn.element.onclick = (): void => {
        if (mediaBtn.element.classList.contains('e-active')) {
            mediaBtn.iconCss = 'e-icons e-pause-icon';
        } else {
            mediaBtn.iconCss = 'e-icons e-play-icon';
        }
    };

    undoBtn.element.onclick = (): void => {
        if (undoBtn.element.classList.contains('e-active')) {
            undoBtn.iconCss = 'e-icons e-redo-icon';
        } else {
            undoBtn.iconCss = 'e-icons e-undo-icon';
        }
    };

    filterBtn.element.onclick = (): void => {
        if (filterBtn.element.classList.contains('e-active')) {
            filterBtn.iconCss = 'e-icons e-filternone-icon';
        } else {
            filterBtn.iconCss = 'e-icons e-filter-icon';
        }
    };

    visibleBtn.element.onclick = (): void => {
        if (visibleBtn.element.classList.contains('e-active')) {
            document.getElementById('content').style.display = 'none';
            visibleBtn.content = 'Show';
            visibleBtn.iconCss = 'e-icons e-show-icon';
        } else {
            document.getElementById('content').style.display = 'block';
            visibleBtn.content = 'Hide';
            visibleBtn.iconCss = 'e-icons e-hide-icon';
        }
    };
}

```

{% endtab %}