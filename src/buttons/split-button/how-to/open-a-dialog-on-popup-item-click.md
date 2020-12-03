---
title: "Open a dialog on popup item click"
component: "SplitButton"
description: "TypeScript SplitButton how to section, group popup items using list view component, dialog open on popup item click."
---

# Open a dialog on popup item click

This section explains about how to open a dialog on SplitButton popup item click. This can be achieved by
handling dialog open in [`select`](../../api/split-button#select) event of the SplitButton.

In the following example, Dialog will open while selecting `Update...` item.

{% tab template= "split-button/dialog", sourceFiles="app.ts,index.html,styles.css", es5Template="dialog-template" %}

```typescript

import { SplitButton, ItemModel, MenuEventArgs } from '@syncfusion/ej2-splitbuttons';
import { Dialog } from '@syncfusion/ej2-popups';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let dialogObj: Dialog = new Dialog({
    width: '250px',
    header: 'Software Update',
    content: 'Are you sure want to update?',
    target: document.getElementById('container'),
    visible: false,
    buttons: [
        {
            click: () => {
                dialogObj.hide();
            },
            buttonModel: { content: 'OK', isPrimary: true }
        },
        {
            click: () =>{
                dialogObj.hide();
            },
            buttonModel: { content: 'Cancel', isPrimary: true }
        }
    ],
});
dialogObj.appendTo('#dialog');

let items: ItemModel[] = [
    {
        text: 'Help'
    },
    {
        text: 'About'
    },
    {
        text: 'Update...'
    }
    ];

let splitBtn: SplitButton = new SplitButton(
    {
        content: 'Help',
        items: items,
        select: (args: MenuEventArgs) => {
            if (args.item.text === 'Update...') {
                dialogObj.show();
            }
        }
    }, '#element');

```

{% endtab %}