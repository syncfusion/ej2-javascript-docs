---
title: "Render model dialog with Rich Text Editor"
component: "Dialog"
description: "This section for Syncfusion Typescript Dialog control explains about, how to Render the model dialog with Rich Text Editor."
---

# Render model dialog with Rich Text Editor

This section explains how to render model dialog with the Rich Text Editor component. when you render model dialog with the Rich Text Editor component, the first row of the content will be hidden because the dialog container and its wrapper elements are styled with display as none. so, the editor’s toolbar does not get proper offset width and rendered above the edit area container. In this scenario, we could use the `refreshUI` method on the Dialog `open` event.

{% tab template="dialog/model-dialog-with-rte",sourceFiles="app.ts,index.html,styles.css", es5Template="model-dialog-with-rte-template" %}

```typescript

import { Dialog } from '@syncfusion/ej2-popups';
import { enableRipple } from '@syncfusion/ej2-base';
import { RichTextEditor, Toolbar, Link, Image, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, HtmlEditor, QuickToolbar);

enableRipple(true);

// Initialize Dialog component
let dialog = new Dialog({
    // Enables modal dialog
    isModal:true,
    // overlayClick event handler
    overlayClick: onOverlayClick,
    // Dialog content
    content: document.getElementById("defaultRTE"),
    // The Dialog shows within the target element
    target: document.getElementById("container"),
    // Dialog width
    width: '500px',
    open: dlgopen
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

let defaultRTE: RichTextEditor = new RichTextEditor( );
defaultRTE.appendTo('#defaultRTE');

function dlgopen() {
    defaultRTE.refreshUI();

}

```

{% endtab %}
