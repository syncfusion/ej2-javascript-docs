# Change menu items dynamically

The items visible in the ContextMenu can be changed dynamically based on the target in which you open the ContextMenu. To achieve this behavior, initialize ContextMenu with all items using [`items`](../../api/context-menu#items) property and then based on the context you open hide/show
required items using [`hideItems`](../../api/context-menu#hideitems)/[`showItems`](../../api/context-menu#showitems) method in [`beforeOpen`](../../api/context-menu#beforeopen) event.

In the following example, the datasource for Clipboard div is `Cut`, `Copy`, `Paste` and for the Editor div is `Add`, `Edit`, `Delete` is changed on [`beforeOpen`](../../api/context-menu#beforeopen) event
using [`hideItems`](../../api/context-menu#hideitems) and [`showItems`](../../api/context-menu#showitems) method.

{% tab template= "context-menu/dynamic", sourceFiles="app.ts,index.html,styles.css",
es5Template="dynamic-template" %}

```typescript

import { ContextMenu, MenuItemModel, ContextMenuModel, BeforeOpenCloseMenuEventArgs } from '@syncfusion/ej2-navigations';
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
    },
    {
        text: 'Add'
    },
    {
        text: 'Edit'
    },
    {
        text: 'Delete'
    }];

// Initialize ContextMenu options.
let menuOptions: ContextMenuModel = {
        target: '#target .e-div',
        items: menuItems,
        beforeOpen: (args: BeforeOpenCloseMenuEventArgs) => {
          // To hide/show items on right click.
          if ((args.event.target as HTMLElement).id === 'right') {
            menuObj.hideItems(['Cut', 'Copy', 'Paste']);
            menuObj.showItems(['Add', 'Edit', 'Delete']);
          } else if ((args.event.target as HTMLElement).id === 'left') {
            menuObj.showItems(['Cut', 'Copy', 'Paste']);
            menuObj.hideItems(['Add','Edit','Delete']);
          }
        }
    };

// Initialize ContextMenu component.
let menuObj: ContextMenu = new ContextMenu(menuOptions, '#contextmenu');

```

{% endtab %}
