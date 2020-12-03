---
title: "Display a dialog with custom position"
component: "Dialog"
description: "Covers customization features such as load content to the dialog from external sources, built-in alert, and confirmation model dialog."
---

# Display a dialog with custom position

By default, the dialog is displayed in the center of the target container. The dialog position can be set using the [position](../../api/dialog/#position) property by providing custom X and Y coordinates.
The dialog can be positioned inside the target based on the given X and Y values.

{% tab template="dialog/dlg-position",sourceFiles="app.ts,index.html,styles.css", es5Template="dlg-position-template" %}

```typescript

import { Dialog } from '@syncfusion/ej2-popups';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let firstDialog = new Dialog({
    // Enables the header
    header: 'Position-01',
    // The Dialog shows within the target element
    target: document.getElementById("container"),
    // Dialog content
    content:'The dialog is positioned at {X: 420, Y: 14} coordinates',
    //Dialog height
    height: '120px',
    //Dialog width
    width: '360px',
    position: {X: 420, Y: 14},
    animationSettings: { effect: 'None' }
});
// Render initialized outer Dialog
firstDialog.appendTo('#firstDialog');

let secondDialog = new Dialog({
    // Enables the header
    header: 'Position-02',
    animationSettings: { effect: 'None'},
    // Dialog content
    content: 'The dialog is positioned at {X: 420, Y: 240} coordinates',
    // The Dialog shows within the target element
    target: document.getElementById("container"),
    // Dialog height
    height: '120px',
    // Dialog Width
    width: '360px',
    position: {X: 420, Y: 240}
});
// Render initialized inner Dialog
secondDialog.appendTo('#secondDialog');

```

{% endtab %}