# Underline a character in the item text

Underline a particular character in a text can be handled in [`beforeItemRender`](../api/context-menu#beforeitemrender) event by
adding `<u>` tag in between the text and given as innerHTML in `li` rendering.

{% tab template= "context-menu/underline", sourceFiles="app.ts,index.html,styles.css",
es5Template="underline-template" %}

```typescript

import { ContextMenu, MenuItemModel, ContextMenuModel, MenuEventArgs } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//Initialize menu items.
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
        target: '#target',
        items: menuItems,
        beforeItemRender: (args: MenuEventArgs) => {
            if (args.item.text === 'Copy') {
                // To underline a particular character.
                args.element.innerHTML = '<u>C</u>opy';
            }
        }
};
// Initialize ContextMenu component.
let menuObj: ContextMenu = new ContextMenu(menuOptions, '#contextmenu');

```

{% endtab %}
