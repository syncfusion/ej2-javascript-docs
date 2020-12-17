---
title: "Resizing"
component: "Dialog"
description: "Explains how to resize the dialog control, where resizing the dialog in all the directions"
---

# Resizing

The Dialog supports resizing feature. To resize the dialog, we have to select and resize it by using its handle (grip) or hovering on any of the edges or borders of the dialog within the sample container.

The resizable dialog can be created by setting the [enableResize](../api/dialog/#enableresize) property to true, which is used to change the size of a dialog dynamically and view its content with expanded mode. The [resizeHandles](../api/dialog/#resizehandles) property can also be configured for all the which directions in which the dialog should be resized. When you configure the target property along with the [enableResize](../api/dialog/#enableresize) property, the dialog can be resized within its specified target container.

{% tab template="dialog/resize",sourceFiles="app.ts,index.html,styles.css", es5Template="resize-template" %}

```typescript

import { Dialog } from '@syncfusion/ej2-popups';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let dialog = new Dialog({
    // Enables the draggable option
    allowDragging: true,
    // Enables the resize option
    enableResize: true,
    // Enables resize in all the direction
    resizeHandles: ['All'],
    // Enables the header
    header: 'Dialog',
    // Dialog content
    content: 'This is a Dialog with resize enabled',
    // Enables the draggable option
    allowDragging: true,
    // Enables the footer buttons,
    buttons: [
        {
            // Click the footer buttons to hide the Dialog
            'click': () => {
                dialog.hide();
            },
            // Accessing button component properties by buttonModel property
            buttonModel:{
                //Enables the primary button
                isPrimary: true,
                content:'OK'
            }
        },
        {
            'click': () => {
                dialog.hide();
            },
            buttonModel:{
                content:'Cancel',
                cssClass:'e-flat'
            }
        }
    ],
    // The Dialog shows within the target element
    target: document.getElementById("container"),
    // Dialog width
    width: '250px',
});
// Render initialized Dialog
dialog.appendTo('#dialog');

// Sample level code to handle the button click action
document.getElementById('targetButton').onclick = (): void => {
    // Call the show method to open the Dialog
     dialog.show();
}
```

{% endtab %}
