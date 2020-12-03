# Change orientation

Orientation in menu items can be changed horizontally or vertically using the [`orientation`](../../api/menu#orientation) property. By default, it is horizontally aligned.

{% tab template= "menu/getting-started", sourceFiles="app.ts,index.html,styles.css",
es5Template="orientation-template", isDefaultActive=true %}

```typescript
import { Menu, MenuItemModel } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//Menu items definition
let menuItems: MenuItemModel[] = [
    {
        text: 'File',
        items: [
            { text: 'Open' },
            { text: 'Save' },
            { text: 'Exit' }
        ]
    },
    {
        text: 'Edit',
        items: [
            { text: 'Cut' },
            { text: 'Copy' },
            { text: 'Paste' }
        ]
    },
    {
        text: 'View',
        items: [
            { text: 'Toolbar' },
            { text: 'Sidebar' },
            { text: 'Full Screen' }
        ]
    },
    {
        text: 'Tools',
        items: [
            { text: 'Spelling & Grammar' },
            { text: 'Customize' },
            { text: 'Options' }
        ]
    },
    { text: 'Help' }
];

// Initialize Menu component.
let menuObj: Menu = new Menu({ orientation: 'Vertical', items: menuItems }, '#menu');
```

{% endtab %}
