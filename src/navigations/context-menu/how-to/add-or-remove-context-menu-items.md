# Add or remove context menu items

ContextMenu items can be added or removed using the [`insertAfter`](../../api/menu#insertafter), [`insertBefore`](../../api/menu#insertbefore) and [`removeItems`](../../api/menu#removeitems) methods.

In the following example, the **Display Settings** menu items are added before the **Personalize** item, the **Sort By** menu items are added after the **Refresh**, and the **Paste** item is removed from context menu.

{% tab template= "context-menu/getting-started", sourceFiles="app.ts,index.html,styles.css",
es5Template="add-remove-template" %}

```typescript
import { ContextMenu, MenuItemModel, ContextMenuModel } from '@syncfusion/ej2-navigations';
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
        text: 'Refresh'
    },
    {
        text: 'Paste'
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
        text: 'Personalize'
    }];

//ContextMenu model definition
let menuOptions: ContextMenuModel = {
    target: '#target',
    items: menuItems
};

let menuObj: ContextMenu = new ContextMenu(menuOptions, '#contextmenu');

menuObj.insertAfter([{text: 'Sort By'}] , 'Refresh');
menuObj.insertBefore([{text: 'Display Settings'}] , 'Personalize');
menuObj.removeItems(['Paste']);

```

{% endtab %}
