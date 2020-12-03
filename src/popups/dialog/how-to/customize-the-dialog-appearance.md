---
title: "Customize the dialog appearance"
component: "Dialog"
description: "Covers customization features such as load content to the dialog from external sources, built-in alert, and confirmation model dialog."
---

# Customize the dialog appearance

You can customize the dialog appearance by providing dialog template as string or HTML element to the [content](../../api/dialog/#content) property. In the following sample, dialog is customized as error window appearance.

{% tab template="dialog/error-dialog",sourceFiles="app.ts,index.html,styles.css", es5Template="error-dialog-template" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
import { Button } from '@syncfusion/ej2-buttons';
import { Dialog } from '@syncfusion/ej2-popups';

let dialogObj: Dialog = new Dialog({
    header: 'File and Folder Rename',
    content: document.getElementById("dlgContent"),
    showCloseIcon: true,
    visible: false,
    buttons: [{
        buttonModel: { isPrimary: true, content: 'Close' }, click:  function() {
            this.hide()
        }
    }],
    target: document.querySelector('body'),
    width: '400px',
    animationSettings: { effect: 'Zoom' },
    beforeOpen: onBeforeopen
});
dialogObj.appendTo('#dialog');

document.getElementById('openBtn').onclick = (): void => {
    dialogObj.show();
};

function onBeforeopen(): void {
    document.getElementById('dlgContent').style.visibility = 'visible';
}

```

{% endtab %}