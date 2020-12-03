# Enable or disable context menu items

You can enable and disable the menu items using the [`enableItems`](../../api/menu#enableitems) method in ContextMenu. To enable menuItems, set the `enable` property in argument to `true` and vice-versa.

In the following example, the **Display Settings** in parent items and **Medium icons** in sub menu items are disabled.

{% tab template="context-menu/getting-started", sourceFiles="app.ts,index.html,styles.css",
 es5Template="enable-template", isDefaultActive=true %}

```typescript

import { ContextMenu, MenuItemModel, ContextMenuModel, BeforeOpenCloseMenuEventArgs } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

//ContextMenu items definition
let menuItems: MenuItemModel[] = [
    {
        text: 'View',
        items: [
          {
            text: 'Large icons'
          },
          {
            text: 'Medium icons'
          },
          {
            text: 'Small icons'
          }
        ]
    },
    {
        text: 'Sort By'
    },
    {
        text: 'Refresh'
    },
    {
        separator: true
    },
    {
        text: 'New'
    },
    {
        separator: true
    },
    {
        text: 'Display Settings'
    },
    {
        text: 'Personalize'
    }];

//ContextMenu model definition
let menuOptions: ContextMenuModel = {
    target: '#target',
    items: menuItems,
    beforeOpen: (args: BeforeOpenCloseMenuEventArgs) => {
      menuObj.enableItems(['Medium icons'], false);
    }
};

let menuObj: ContextMenu = new ContextMenu(menuOptions, '#contextmenu');

menuObj.enableItems(['Display Settings'], false);

```

{% endtab %}

> To disable sub menu items, use the [`beforeOpen`](../../api/menu#beforeopen) event.