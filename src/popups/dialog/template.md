---
title: "Template"
component: "Dialog"
description: "Explains how to customize the dialog's user interface (UI) elements such as header, footer, and content using a template."
---

# Template

In Dialog the template support is provided to the header and footer sections. So any text or HTML content can be appending in these sections.

## Header

The Dialog header content can be provided through the
[`header`](../api/dialog/#header) property, and it will allow both text and any HTML content as a string.
Also in header, close button is provided as built-in support, and this can be enabled through
the [`showCloseIcon`](../api/dialog/#showcloseicon) property.

## Footer

The Dialog footer can be enabled by adding built-in [`buttons`](../api/dialog/#buttons) or providing any HTML string through the [`footerTemplate`](../api/dialog/#footertemplate).

> The [`buttons`](../api/dialog/#buttons) and [`footerTemplate`](../api/dialog/#footertemplate) properties can't be used at the same time.

## Content

The Dialog content can be provided through the [`content`](../api/dialog/#content) property, and it accepts both text and HTML string as content.

The below example demonstrates the usage of header, footer and content templates in the Dialog control.

{% tab template="dialog/template",sourceFiles="app.ts,index.html,styles.css",es5Template="templates-template" %}

```typescript

import { Dialog } from '@syncfusion/ej2-popups';
import { Button } from '@syncfusion/ej2-buttons';
/**
 * Dialog template sample
 */

let icontemp: string = '<button id="sendButton" class="e-control e-btn e-primary" data-ripple="true">' + 'Send</button>';
let headerimg: string = '<img class="img2" style="display: inline-block;" src="https://ej2.syncfusion.com/products/typescript/dialog/template/images/1.png" alt="header image">';
let sendbutton: Button = new Button();
let proxy: any = this;

// Initialize Dialog component
let dialog = new Dialog({
    // Enables the header with template content
    header: headerimg + '<div class="dlg-template" title="Nancy" class="e-icon-settings"> Nancy </div>',
    // Enables the footer with template content
    footerTemplate: ' <input id="inVal" class="e-input" type="text" placeholder="Enter your message here!"/>' + icontemp,
    // Dialog content
    content: document.getElementById("dlgContent"),
    // Enables the close icon button in header
    showCloseIcon: true,
    // The Dialog shows within the target element
    target: document.getElementById("container"),
    //Dialog width
    width: '400px',
    height: '250px',
    beforeOpen: onBeforeopen
});
// Render initialized Dialog
dialog.appendTo('#dialog');
sendbutton.appendTo('#sendButton');

// Sample level code to handle the button click action
document.getElementById('targetButton').onclick = (): void => {
    // Call the show method to open the Dialog
    dialog.show();
}

(document.getElementById('sendButton')as HTMLElement).onkeydown = (e: any) => {
    if (e.keyCode === 13) { updateTextValue(); }
};

(document.getElementById('inVal')as HTMLElement).onkeydown = (e: any) => {
    if (e.keyCode === 13) { updateTextValue(); }
};

document.getElementById('sendButton').onclick = (): void => {
    updateTextValue();
};

function onBeforeopen(): void {
    document.getElementById('dlgContent').style.visibility = 'visible';
}

function updateTextValue () : void {
    let enteredVal: HTMLInputElement = document.getElementById('inVal') as HTMLInputElement;
    let dialogTextElement: HTMLElement = document.getElementsByClassName('dialogText')[0] as HTMLElement;
    let dialogTextWrap : HTMLElement = document.getElementsByClassName('dialogContent')[0] as HTMLElement;
    if (enteredVal.value !== '') {
        dialogTextElement.innerHTML = enteredVal.value;
        enteredVal.value = '';
    }
}

```

{% endtab %}

## See Also

* [How to add an icon to dialog buttons](./how-to/add-an-icons-to-dialog-buttons)
* [How to customize the dialog appearance](./how-to/customize-the-dialog-appearance)
