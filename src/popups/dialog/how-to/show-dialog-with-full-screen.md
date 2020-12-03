---
title: "Show dialog with full screen"
component: "Dialog"
description: "Covers customization features such as load content to the dialog from external sources, built-in alert, and confirmation model dialog."
---

# Show dialog with fullscreen

You can show the dialog in fullscreen by passing `true` as argument to the dialog `show` method. By using [visible](../../api/dialog/#visible) property you can prevent the dialog from initially shown.

{% tab template="dialog/dlg-fullscreen",sourceFiles="app.ts,index.html,styles.css", es5Template="dlg-fullscreen-template" %}

```typescript

import { Dialog } from '@syncfusion/ej2-popups';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize Dialog component
let dialog = new Dialog({
    // Enables the footer buttons
    buttons: [
        {
            // Click the footer buttons to hide the Dialog
            'click': () => {
                dialog.hide();
            },
            // Accessing button component properties by buttonModel property
            buttonModel: {
                //Enables the primary button
                isPrimary: true,
                cssClass: 'e-flat',
                content: 'OK'
            }
        },
        {
            'click': () => {
                dialog.hide();
            },
            buttonModel: {
                content: 'Cancel',
                cssClass: 'e-flat'
            }
        }
    ],
    // Enables the header
    header: 'Dialog',
    // Dialog content
    content: 'This is a Dialog with fullscreen display',
    // The Dialog shows within the target element
    target: document.getElementById("container"),
    // Dialog width
    width: '250px',
    visible:false,
});
// Render initialized Dialog
dialog.appendTo('#dialog');
// Sample level code to handle the button click action
document.getElementById('targetButton').onclick = (): void => {
    // Call the show method to open the Dialog
    dialog.show(true);
}

```

{% endtab %}