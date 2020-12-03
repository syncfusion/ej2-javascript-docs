---
title: "Position the Dialog on center of the page on scrolling"
component: "Dialog"
description: "Covers customization features such as load content to the dialog from external sources, built-in alert, and confirmation model dialog."
---

# Position the Dialog on center of the page on scrolling

By default, when scroll the page/container Dialog also scrolled along with the page/container.
When a user expects to display the Dialog in the same position without scrolling achieving this in
sample level as like below. Here added 'e-fixed' class to Dialog element by using [cssClass](../../api/dialog/#cssclass) property and prevent the scrolling.

{% tab template="dialog/scrollposition",sourceFiles="app.ts,index.html,styles.css", es5Template="scroll-template" %}

```typescript

import { Dialog } from '@syncfusion/ej2-popups';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize Dialog component
let dialog = new Dialog({
    // Enables the header
    header: 'Dialog',
    // Dialog content
    content: document.getElementById("dlgContent"),
    // Disable the Esc key to hide the Dialog
    closeOnEscape: false,
    // The Dialog shows within the target element
    target: document.getElementById("container"),
    // Dialog width
    width: '250px',
    beforeOpen: onBeforeopen
});
// Render initialized Dialog
dialog.appendTo('#dialog');

// Sample level code to prevent Dialog scrolling
document.getElementById('targetButton').onclick = (): void => {
    dialog.cssClass = 'e-fixed';
}

function onBeforeopen(): void {
    document.getElementById('dlgContent').style.visibility = 'visible';
}

```

{% endtab %}