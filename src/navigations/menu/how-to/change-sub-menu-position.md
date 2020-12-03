# Change sub menu position

The submenu position can be changed by using the [`beforeOpen`](../../api/menu/#beforeopen) event. Assign the top and left position where you want to open the submenu to the [`beforeOpen`](../../api/menu/#beforeopen) event arguments `args.top` and `args.left` respectively.

In the below sample, the sub menu opens above the parent menu item.

{% tab template="menu/position", sourceFiles="app.ts,index.html, styles.css",
 es5Template="position-template", isDefaultActive=true %}

```typescript
import { Menu, MenuItemModel, MenuModel } from '@syncfusion/ej2-navigations';
import { BeforeOpenCloseMenuEventArgs } from '@syncfusion/ej2-navigations';
import { enableRipple, closest } from '@syncfusion/ej2-base';

enableRipple(true);

// Menu items definition
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

// Menu model definitions
let menuOptions: MenuModel = {
    items: menuItems,
    beforeOpen: (args: BeforeOpenCloseMenuEventArgs) => {
        // Getting parent menu item element offset
        let relativeOffset: ClientRect = closest(args.event.target as Element, '.e-menu-item').getBoundingClientRect();
        // Getting sub menu wrapper element using closest method
        let subMenuEle: HTMLElement = closest(args.element, '.e-menu-wrapper') as HTMLElement;
        subMenuEle.style.display = 'block';
        args.top = (relativeOffset.top - subMenuEle.getBoundingClientRect().height) + pageYOffset;
        args.left = relativeOffset.left + pageXOffset;
        subMenuEle.style.display = '';
    }
};

// Initialize Menu component
new Menu(menuOptions, '#menu');
```

{% endtab %}

>> For custom positioning, set both `top` and `left` position in the [`beforeOpen`](../../api/menu/#beforeopen) event.