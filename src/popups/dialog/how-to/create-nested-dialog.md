---
title: "Create Nested Dialog"
component: "Dialog"
description: "Covers customization features such as load content to the dialog from external sources, built-in alert, and confirmation model dialog."
---

# Create Nested Dialog

A Dialog can be nested within another Dialog. The below sample contains parent and child Dialog (inner Dialog).

**Step 1**:

Create two div elements with id `#dialog` and `#innerDialog`.

**Step 2**:

Initialize the Dialog as mentioned in the below sample.

**Step 3**:

Set the inner Dialog target as `#dialog`.

{% tab template="dialog/nested",sourceFiles="app.ts,index.html,styles.css", es5Template="nested-template" %}

```typescript
import { Dialog } from '@syncfusion/ej2-popups';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize the Outer Dialog component
let dialog = new Dialog({
    // Enables the header
    header: 'Outer Dialog',
    // Enables the close icon button in header
    showCloseIcon: true,
    // The Dialog shows within the target element
    target: document.getElementById("container"),
    // Dialog content
    content: document.getElementById("dlgContent"),
    //Dialog height
    height: '300px',
    animationSettings: { effect: 'None' },
    // Disable the Esc key option to hide the Dialog
    closeOnEscape: false,
    //Dialog width
    width: '400px',
    // Dialog beforeOpen event
    beforeOpen: onBeforeopen
});
// Render initialized outer Dialog
dialog.appendTo('#dialog');

// Sample level code to handle the button click action
document.getElementById('targetButton').onclick = (): void => {
    // Call the show method to open the Dialog
    dialog.show();
}

// initialize the Inner Dialog component
let innerDialog = new Dialog({
    // Enables the header
    header: 'Inner Dialog',
    // Enables the close icon button in header
    showCloseIcon: true,
    animationSettings: { effect: 'None'},
    // Disable the Esc key option to hide the Dialog
    closeOnEscape: false,
    // Dialog content
    content: 'This is a Nested Dialog',
    // InnerDialog target as outerDialog
    target: document.getElementById("dialog"),
    // Dialog height
    height: '150px',
    // Dialog Width
    width: '250px'
});

document.getElementById('innerButton').onclick = (): void => {
    // Call the show method to open the Dialog
    innerDialog.show();
}
// Render initialized inner Dialog
innerDialog.appendTo('#innerDialog');

function onBeforeopen(): void {
    document.getElementById('dlgContent').style.visibility = 'visible';
}

```

{% endtab %}