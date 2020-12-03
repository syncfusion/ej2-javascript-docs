---
title: "Center the dialog based on current scroll position"
component: "Dialog"
description: "This section explains how to center the dialog based on the current scroll position."
---

# Center the dialog based on the current scroll position

The dialog is always centered based on the target container. If the target is not specified, then the dialog will be rendered based on its body and centered in the position of the current viewpoint.

In the following sample, the model dialog is centered based on its current scroll position of the page.

{% tab template="dialog/center-the-dialog",sourceFiles="app.ts,index.html,styles.css", es5Template="center-the-dialog-template" %}

```typescript

import { Dialog } from '@syncfusion/ej2-popups';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize Dialog component
let dialog = new Dialog({
    // Enables modal dialog
    isModal:true,
    // overlayClick event handler
    overlayClick: onOverlayClick,
    // Dialog content
    content: 'This is a modal dialog',
    // The Dialog shows within the target element
    target: document.body,
    // Dialog width
    width: '250px'
});
// Render initialized Dialog
dialog.appendTo('#dialog');

// Sample level code to handle the button click action
document.getElementById('targetButton').onclick = (): void => {
    // Call the show method to open the Dialog
    dialog.show();
}

// Sample level code to hide the Dialog when click the Dialog overlay
function onOverlayClick() {
    dialog.hide();
}

```

{% endtab %}