# Open a dialog on ContextMenu item click

This section explains about how to open a dialog on ContextMenu item click. This can be achieved by
handling dialog open in [`select`](../api/context-menu/#select) event of the ContextMenu.

In the following sample, Dialog will open while clicking `Save As...` item.

{% tab template= "context-menu/dialogopen", sourceFiles="app.ts,index.html,styles.css",
es5Template="dialogopen-template" %}

```typescript
import { ContextMenu, MenuEventArgs, MenuItemModel } from '@syncfusion/ej2-navigations';
import { ListView, ListViewModel } from '@syncfusion/ej2-lists';
import { Dialog } from '@syncfusion/ej2-popups';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// To initialize Dialog component.
let dialog: Dialog = new Dialog({
    content: "This file can be saved as PDF",
    buttons: [{
        buttonModel: {
            isPrimary: true,
            content: 'Submit',
            cssClass: 'e-flat',
        },
        click: function () {
            this.hide();
        }
    }],
    target: document.getElementById("container"),
    width: '200px',
    height: '110px',
    visible: false
});

// Render initialized dialog.
dialog.appendTo('#dialog');

// Initialize menu items.
let menuItems: MenuItemModel[] = [
    {
        text: 'Back'
    },
    {
        text: 'Forward'
    },
    {
        text: 'Reload'
    },
    {
        separator: true
    },
    {
        text: 'Save As...'
    },
    {
        text: 'Print'
    },
    {
        text: 'Cast'
    }];

// Initialize ContextMenu options.
let menuOptions: ContextMenu = {
    target: '#target',
    items: menuItems,
    select: (args: MenuEventArgs) => {
       if(args.item.text === 'Save As...') {
           dialog.show();
       }
    }
};

// Initialize ContextMenu component.
let menuObj: ContextMenu = new ContextMenu(menuOptions, '#contextmenu');

```

{% endtab %}
