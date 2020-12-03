# Open and close ContextMenu

Open and close the ContextMenu manually whenever required by using the open and close methods.

In the following sample, the ContextMenu is opened using the [`open`](../../api/context-menu#open) method at the specified position with `X` and `Y` coordinates and to close the ContextMenu, [`close`](../../api/context-menu#close) method is called internally on ContextMenu item click or document click.

{% tab template= "context-menu/how-to/open-and-close", sourceFiles="app.ts,index.html,styles.css", es5Template="open-method-template" %}

```typescript
import { ContextMenu, MenuItemModel, ContextMenuModel } from '@syncfusion/ej2-navigations';
import { Button } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize menu items.
let menuItems: MenuItemModel[] = [
    {
        text: 'Cut'
    },
    {
        text: 'Copy'
    },
    {
        text: 'Paste'
    }];

// Initialize ContextMenu options.
let menuOptions: ContextMenuModel = {
    items: menuItems
};

// Initialize ContextMenu component.
let menuObj: ContextMenu = new ContextMenu(menuOptions, '#contextmenu');

// Initialize Button component.
let button: Button = new Button();
// Render initialized Button.
button.appendTo('#btnElement');

// To position ContextMenu on Button click.
document.getElementById('btnElement').onclick=function() {
   menuObj.open(60, 20);
}

```

{% endtab %}
