---
title: "Prevent the focus on the first element"
component: "Dialog"
description: "Covers customization features such as load content to the dialog from external sources, built-in alert, and confirmation model dialog."
---

# Prevent the focus on the first element

By default, the dialog focuses on the first elements of the content area which can be active and focusable. You can prevent this default focusing behavior using the [open](../../api/dialog/#open) event and by enabling the `preventFocus` argument.

Bind the open event and enable the preventFocus argument within an event like the below sample.

{% tab template="dialog/dlg-focus",sourceFiles="app.ts,index.html", es5Template="dlg-focus-template" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
import { Button } from '@syncfusion/ej2-buttons';
import { Dialog, OpenEventArgs } from '@syncfusion/ej2-popups';

let dialogObj: Dialog = new Dialog({
    header: "Sign In",
    buttons: [{ buttonModel: { isPrimary: true, content: 'Yes' }, click: btnClick }, { buttonModel: { content: 'No'}, click: btnClick }],
    target: document.getElementById("container"),
    height: 'auto',
    width: '300px',
    open: onOpen
});
dialogObj.appendTo('#dialog');

document.getElementById('targetButton').onclick = (): void => {
    dialogObj.show();
};

function btnClick() {
    dialogObj.hide();
}

function onOpen(args: OpenEventArgs) {
  args.preventFocus = true;
}

```

{% endtab %}