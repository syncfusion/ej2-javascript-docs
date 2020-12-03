---
title: "ContextMenu Icons and Navigation"
component: "ContextMenu"
description: "TypeScript ContextMenu allows the end user to place the icons on menu items and navigate to other webpages while clicking the menu items."
---

# Icons and Navigation

## Icons

The ContextMenu item have an icon/image in it to provide visual representation of the action.
To place the icon on a menu item, set the [`iconCss`](../api/context-menu/menuItemModel#iconcss)
property to e-icons with the required icon CSS. By default, the icon is positioned to the left
side of the menu item. In the following sample, the icons for Cut, Copy and Paste menu items are
added using the `iconCss` property.

{% tab template="context-menu/icons", sourceFiles="app.ts,index.html,styles.css",
es5Template="icons-template", isDefaultActive=true %}

```typescript
import { ContextMenu, MenuItemModel, ContextMenuModel } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize menu items.
let menuItems: MenuItemModel[] = [
    {
        text: 'Cut',
        iconCss: 'e-db-icons e-cut'
    },
    {
        text: 'Copy',
        iconCss: 'e-icons e-copy'
    },
    {
        text: 'Paste',
        iconCss: 'e-db-icons e-paste',
    }];

// Initialize ContextMenu options.
let menuOptions: ContextMenuModel = {
        target: '#target',
        items: menuItems
    };

// Initialize ContextMenu component.
let menuObj: ContextMenu = new ContextMenu(menuOptions, '#contextmenu')
```

{% endtab %}

## Navigation

Navigation in ContextMenu is usage to navigate to the other web page when menu item is
clicked. This can be achieved by providing link to the menu item using the
[`url`](../api/context-menu/menuItemModel#url) property.
In the following sample, Navigation URL for Flipkart, Amazon, and Snapdeal menu items
are added using the `url` property.

{% tab template= "context-menu/navigation", sourceFiles="app.ts,index.html,styles.css",
es5Template="navigation-template" %}

```typescript
import { ContextMenu, MenuEventArgs, MenuItemModel, ContextMenuModel } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize menu items.
let menuItems: MenuItemModel[] = [
    {
        text: 'Flipkart',
        iconCss: 'e-cart-icon e-link',
        url: 'https://www.google.co.in/search?q=flipkart'
    },
    {
        text: 'Amazon',
        iconCss: 'e-cart-icon e-link',
        url: 'https://www.google.co.in/search?q=amazon'
    },
    {
        text: 'Snapdeal',
        iconCss: 'e-cart-icon e-link',
        url: 'https://www.google.co.in/search?q=snapdeal'
    }];

// Initialize ContextMenu options.
let menuOptions: ContextMenuModel = {
        target: '#target',
        items: menuItems,
        // To open url in blank page.
        beforeItemRender: (args: MenuEventArgs) => {
            args.element.getElementsByTagName('a')[0].setAttribute('target', '_blank');
        }
    };

// Initialize the ContextMenu component.
let menuObj: ContextMenu = new ContextMenu(menuOptions, '#contextmenu')
```

{% endtab %}

> To open the links in new tab, set `target` attribute with the value `_blank` in the [`beforeItemRender`](../api/context-menu#beforeitemrender) event.

## See Also

* [How to change menu items dynamically](./how-to/change-menu-items-dynamically)
