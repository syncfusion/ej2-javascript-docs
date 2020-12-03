---
title: "ContextMenu Accessibility"
component: "ContextMenu"
description: "TypeScript ContextMenu component has accessibility support to help access the features via keyboard, on-screen readers, or other assistive technology devices."
---

# Accessibility

## ARIA attributes

The web accessibility makes web content and web applications more accessible for people with disabilities. It especially helps in dynamic content change and development of advanced user interface controls with AJAX, HTML, JavaScript, and related technologies.
ContextMenu provides built-in compliance with `WAI-ARIA` specifications. `WAI-ARIA` support is achieved through the attributes like `aria-expanded` and `aria-haspopup` applied for menu item in
ContextMenu. It helps the people with disabilities by providing information about the widget for assistive
technology in the screen readers. ContextMenu component contains the `menu` role and `menuItem` role.

| Properties | Functionality |
| ------------ | ----------------------- |
| menu | This role will be specified for an item which have sub menu. |
| menuItem | This role will be specified for an item that do not have sub menus. |
| aria-haspopup | Indicates the availability and type of interactive popup element. |
| aria-expanded | Indicates whether the subtree can be expanded or collapsed, as well as indicates whether its current state is expanded or collapsed. |

## Keyboard interaction

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td>
<b>Keyboard shortcuts</b></td><td>
<b>Actions</b></td></tr>
<tr>
<td>
<kbd>Esc</kbd></td><td>
Closes the opened ContextMenu.</td></tr>
<tr>
<td>
<kbd>Enter</kbd></td><td>
Selects the focused item.</td></tr>
<tr>
<td>
<kbd>Up</kbd></td><td>
Navigates up or to the previous menu item.</td></tr>
<tr>
<td>
<kbd>Down</kbd></td><td>
Navigates down or to the next menu item.</td></tr>
<tr>
<td>
<kbd>Left</kbd></td><td>
Close the current sub menu and navigates to the parent menu.</td></tr>
<tr>
<td>
<kbd>Right</kbd></td><td>
Navigates and open the next sub menu.</td></tr>
</table>

{% tab template= "context-menu/accessibility", sourceFiles="app.ts,index.html,styles.css",
es5Template="accessibility-template", isDefaultActive=true %}

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
        items: [
            {
                text: 'Paste Text',
                iconCss: 'e-cm-icons e-pastetext'
            },
            {
                text: 'Paste Special',
                iconCss: 'e-cm-icons e-pastespecial'
            } ]
    }];

// Initialize ContextMenu options.
let menuOptions: ContextMenuModel = {
        items: menuItems,
        target: '#target'
    };

// Initialize ContextMenu component.
let menuObj: ContextMenu = new ContextMenu(menuOptions, '#contextmenu');

// To open ContextMenu at specified position.
menuObj.open(40, 20);

```

{% endtab %}