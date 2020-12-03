# Right-To-Left

Menu component has RTL support. This can be achieved by setting [`enableRtl`](../../api/menu#enablertl) as `true`.

The following example illustrates how to enable right-to-left support in Menu component.

{% tab template= "menu/getting-started", sourceFiles="app.ts,index.html,styles.css",
es5Template="rtl-template", isDefaultActive=true %}

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
            { text: 'Sidebar' }
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
    { text: 'Go' },
    { text: 'Help' }
];

// Initialize Menu component.
let menuObj: Menu = new Menu({ items: menuItems, enableRtl: true }, '#menu');
```

{% endtab %}