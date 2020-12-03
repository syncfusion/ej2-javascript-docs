---
title: "Add an icons to dialog buttons"
component: "Dialog"
description: "Covers customization features such as load content to the dialog from external sources, built-in alert, and confirmation model dialog."
---

# Add an icons to dialog buttons

You can add an icons to the dialog buttons using the [buttons](../../api/dialog/#buttons) property or [footerTemplate](../../api/dialog/#footertemplate) property . For detailed information about dialog buttons, refer to the [documentation](../../api/dialog/#buttons)&nbsp;section.

In the following sample, dialog footer buttons are customized with icons using `buttons` property.

{% tab template="dialog/dialog-button-icons",sourceFiles="app.ts,index.html", es5Template="dialog-button-template" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
import { Button } from '@syncfusion/ej2-buttons';
import { Dialog } from '@syncfusion/ej2-popups';

let dialogObj: Dialog = new Dialog({
    header: 'Delete Multiple Items',
    content: "Are you sure you want to permanently delete all of these items?",
    showCloseIcon: true,
    buttons: [{ buttonModel: { isPrimary: true, content: 'Yes', iconCss: 'e-icons e-ok-icon' }, click: btnClick }, { buttonModel: { content: 'No', iconCss: 'e-icons e-close-icon' }, click: btnClick }],
    target: document.body,
    height: 'auto',
    width: '300px',
    animationSettings: { effect: 'Zoom' },
    closeOnEscape: true
});
dialogObj.appendTo('#dialog');

document.getElementById('openBtn').onclick = (): void => {
    dialogObj.show();
};

function btnClick() {
    dialogObj.hide();
}

```

{% endtab %}

In the following sample, dialog footer buttons are customized with icons using `footerTemplate` property.

{% tab template="dialog/dialog-footer-icons",sourceFiles="app.ts,index.html", es5Template="dialog-footer-icons-template" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
import { Button } from '@syncfusion/ej2-buttons';
import { Dialog } from '@syncfusion/ej2-popups';

let dialogObj: Dialog = new Dialog({
    header: 'Delete Multiple Items',
    content: "Are you sure you want to permanently delete all of these items?",
    showCloseIcon: true,
    footerTemplate: '<button id="Button1" class="e-control e-btn e-primary e-flat" data-ripple="true"><span class="e-btn-icon e-icons e-ok-icon e-icon-left"></span>Yes</button><button id="Button2" class="e-control e-btn e-flat" data-ripple="true"><span class="e-btn-icon e-icons e-close-icon e-icon-left"></span>No</button>',
    target: document.body,
    height: 'auto',
    width: '300px',
    animationSettings: { effect: 'Zoom' },
    closeOnEscape: true
});
dialogObj.appendTo('#dialog');

document.getElementById('openBtn').onclick = (): void => {
    dialogObj.show();
};

document.getElementById('Button1').onclick = (): void => {
    dialogObj.hide();
};

document.getElementById('Button2').onclick = (): void => {
    dialogObj.hide();
};

```

{% endtab %}