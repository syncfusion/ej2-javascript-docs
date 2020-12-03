---
title: "Open a dialog on popup item click"
component: "DropDownButton"
description: "TypeScript DropDownButton how to section, hide drop down arrow, group popup items using list view component, dialog open on popup item click."
---

# Open a dialog on popup item click

This section explains about how to open a dialog on DropdownButton popup item click. This can be achieved by
handling dialog open in [`select`](../../api/drop-down-button#select) event of the DropdownButton.

In the following example, Dialog will open while selecting `Other Folder...` item.

{% tab template= "drop-down-button/dialog", sourceFiles="app.ts,index.html,styles.css",
es5Template="dialog-template" %}

```typescript
import { DropDownButton, ItemModel, MenuEventArgs, DropDownButtonModel } from '@syncfusion/ej2-splitbuttons';
import { Dialog } from '@syncfusion/ej2-popups';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// To initialize the Dialog component.
let dialog: Dialog = new Dialog({
    content: "Move Items To 'Web Team'",
    header: 'Move Items',
    buttons: [{
        buttonModel: {
            isPrimary: true,
            content: 'OK',
            cssClass: 'e-flat',
        },
        click: function () {
            this.hide();
        }
    }],
    width: '250px',
    height: '150px',
    visible: false,
    position: {X: 100, Y: 100}
});

// Render initialized Dialog.
dialog.appendTo('#dialog');

// Initialize action items.
let items: ItemModel[] = [
    {
        text: 'Archive'
    },
    {
        text: 'Inbox'
    },
    {
        text: 'HR Portal'
    },
    {
        separator: true
    },
    {
        text: 'Other Folder...'
    },
    {
        text: 'Copy to Folder'
    }];

// Initialize DropDownButton options.
let ddbOption: DropDownButtonModel = {
  iconCss: 'ddb-icons e-folder',
  cssClass: 'e-vertical',
  items: items,
  iconPosition: 'Top',
  select: (args: MenuEventArgs) => {
      if (args.item.text === 'Other Folder...') {
        dialog.show();
      }
  }
};
// To initialize the DropDownButton component.
let drpDownBtn: DropDownButton = new DropDownButton(ddbOption, '#iconbutton');

```

{% endtab %}