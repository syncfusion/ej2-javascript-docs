---
title: "Prevent closing of modal dialog"
component: "Dialog"
description: "Covers customization features such as load content to the dialog from external sources, built-in alert, and confirmation model dialog."
---

# Prevent closing of modal dialog

You can prevent closing of modal dialog by setting the [beforeClose](../../api/dialog/#beforeclose) event argument cancel value to true.
In the following sample, the dialog is closed when you enter the username value with minimum 4 characters. Otherwise, it will not be closed.

{% tab template="dialog/dlg-validation",sourceFiles="app.ts,index.html,styles.css", es5Template="dlg-validation-template" %}

```typescript

import { Dialog } from '@syncfusion/ej2-popups';
import { enableRipple } from '@syncfusion/ej2-base';

// To get the all input fields and its container.
let inputElement = document.querySelectorAll('.e-input-group .e-input,.e-float-input.e-input-group input');

// Add 'e-input-focus' class to the input for achive ripple effect when focus on the input field.
for (let i = 0; i < inputElement.length; i++) {
    inputElement[i].addEventListener("focus", function () {
        let parentElement = this.parentNode;
        if (parentElement.classList.contains('e-input-in-wrap')) {
            parentElement.parentNode.classList.add('e-input-focus');
        } else {
            this.parentNode.classList.add('e-input-focus');
        }
    });
    inputElement[i].addEventListener("blur", function () {
        let parentElement = this.parentNode;
        if (parentElement.classList.contains('e-input-in-wrap')) {
            parentElement.parentNode.classList.remove('e-input-focus');
        } else {
            this.parentNode.classList.remove('e-input-focus');
        }
    });
}

// Add 'e-input-btn-ripple' class to the icon element for achive ripple effect when click on the icon.
var inputIcon = document.querySelectorAll('.e-input-group-icon');
for (let i = 0; i < inputIcon.length; i++) {
    inputIcon[i].addEventListener('mousedown', function () {
        this.classList.add('e-input-btn-ripple');
    });
    inputIcon[i].addEventListener('mouseup', function () {
        let element = this;
        setTimeout(function () {
            element.classList.remove('e-input-btn-ripple');
        }, 500);
    });
}

enableRipple(true);

// Initialize Dialog component
let dialog: Dialog = new Dialog({
    // Enables the header
    header: 'Sign in',
    // Dialog content
    content: document.getElementById("dlgContent"),
    // Enables the footer buttons
    buttons: [{
        // Accessing button component properties by buttonModel property
        buttonModel: {
            //Enables the primary button
            isPrimary: true,
            content: 'Log in',
            cssClass: 'e-primary',
        },
        // Click the footer buttons to hide the Dialog
        click: function () {
            this.hide();
        }
    }],
    // The Dialog shows within the target element
    target: document.getElementById("container"),
    // Dialog width
    width: '300px',
    beforeClose: validation,
    isModal: true,
    beforeOpen: onBeforeopen
});
// Render initialized Dialog
dialog.appendTo('#dialog');

document.getElementById('targetButton').onclick = (): void => {
    dialog.show();
    document.getElementById("textvalue").value = "";
    document.getElementById("textvalue2").value = "";
};

function validation(args) {
    let text = document.getElementById('textvalue');
    let text1 = document.getElementById('textvalue2');
    if (text.value === "" && text1.value === "") {
        args.cancel= true;
        alert("Enter the username and password")
    } else if (text.value === "") {
        args.cancel= true;
        alert("Enter the username")
    } else if (text1.value === "") {
        args.cancel= true;
        alert("Enter the password")
    } else if (text.value.length < 4) {
        args.cancel= true;
        alert("Username must be minimum 4 characters")
    } else {
        args.cancel= false;
        document.getElementById("textvalue").value = "";
        document.getElementById("textvalue2").value = "";
    }
}

function onBeforeopen(): void {
    document.getElementById('dlgContent').style.visibility = 'visible';
}

```

{% endtab %}