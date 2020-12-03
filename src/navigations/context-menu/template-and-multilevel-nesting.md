---
title: "ContextMenu Template and  Multilevel Nesting"
component: ContextMenu""
description: "TypeScript ContextMenu allows the end user to customize the menu items, and supports multiple level of nesting."
---

# Template and Multilevel nesting

## Template

The ContextMenu items can be customized by using the [`beforeItemRender`](../api/context-menu#beforeitemrender) event. The item render event
triggers while rendering each menu item. The event argument will be used to identify the menu
item and customize it based on the requirement. In the following sample, the menu item is rendered with keycode for specified action in ContextMenu using the template. Here, the keycode is specified for Save as,
View page source, and Inspect in the right side corner of the menu items by adding span element in the [`beforeItemRender`](../api/context-menu#beforeitemrender) event.

{% tab template= "context-menu/template", sourceFiles="app.ts,index.html,styles.css",
es5Template="contextmenu-template", isDefaultActive=true %}

```typescript
import { createElement, enableRipple } from '@syncfusion/ej2-base';
import { ContextMenu, MenuEventArgs, MenuItemModel, ContextMenuModel } from '@syncfusion/ej2-navigations';

enableRipple(true);

// Initialize menu items.
let menuItems: MenuItemModel[] = [
    {
        text: 'Save as...'
    },
    {
        text: 'View page source'
    },
    {
        text: 'Inspect'
    }];

// Initialize ContextMenu options.
let menuOptions: ContextMenuModel = {
        target: '#target',
        items: menuItems,
        beforeItemRender: (args: MenuEventArgs) => {
            // To render template in li.
            let shortCutSpan: HTMLElement = createElement('span');
            let text: string = args.item.text;
            let shortCutText: string = text === 'Save as...' ? 'Ctrl + S' : (text === 'View page source' ?
            'Ctrl + U'      : 'Ctrl + Shift + I');
            shortCutSpan.textContent = shortCutText;
            args.element.appendChild(shortCutSpan);
            shortCutSpan.setAttribute('class','shortcut');
        }
    };

// Initialize ContextMenu component.
let menuObj: ContextMenu = new ContextMenu(menuOptions, '#contextmenu');
```

{% endtab %}

> To create span element, `createElement` utility function used from `ej2-base`.

## Multilevel nesting

The Multiple level nesting supports in ContextMenu. It can be achieved by mapping the [`items`](../api/context-menu/menuItemModel#items) property inside the parent [`menuItems`](../api/context-menu#items). In the below sample, three level nesting of ContextMenu is provided.

{% tab template= "context-menu/getting-started", sourceFiles="app.ts,index.html,styles.css",
es5Template="multilevel-template" %}

```typescript
import { ContextMenu, MenuItemModel, ContextMenuModel } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize menu items.
let menuItems: MenuItemModel[] = [
        {
            text: 'Show All Bookmarks',
        },
        {
            text: 'Bookmarks Toolbar',
            items: [
                {
                    text: 'Most Visited',
                    items: [
                    {
                        text: 'Google',
                    },
                    {
                        text: 'Gmail'
                    }]
                },
                {
                    text: 'Recently Added'
                }
            ]
        }];

// Initialize ContextMenu options.
let menuOptions: ContextMenuModel = {
        target: '#target',
        items: menuItems
    };

// Initialize ContextMenu component.
let menuObj: ContextMenu = new ContextMenu(menuOptions, '#contextmenu');

```

{% endtab %}

> To open sub menu items only on click, [`showItemOnClick`](../api/context-menu#showitemonclick) property should be set as `true`.

## See Also

* [Populate menu items with data source](./how-to/populate-menu-items-with-data-source)
