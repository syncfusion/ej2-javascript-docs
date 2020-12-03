# Customize menu items

## Add or remove menu items

Menu items can be added or removed using the [`insertAfter`](../../api/menu#insertafter), [`insertBefore`](../../api/menu#insertbefore) and [`removeItems`](../../api/menu#removeitems) methods.

In the following example, the **Europe** menu items are added before the **Oceania** item, the **Africa** menu items are added after the **Asia**, and the **South America** and **Mexico** items are removed from menu.

{% tab template= "menu/getting-started", sourceFiles="app.ts,index.html,styles.css",
es5Template="add-remove-template", isDefaultActive=true %}

```typescript
import { Menu, FieldSettingsModel } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//Menu datasource
let data:  { [key: string]: Object }[] = [
    {
        continent: 'Asia',
        countries: [
            { country: 'China' },
            { country: 'India' },
            { country: 'Japan' }
        ]
    },
    {
        continent: 'North America',
        countries: [
            { country: 'Canada' },
            { country: 'Mexico' },
            { country: 'USA' }
        ]
    },
    {
        continent: 'South America',
        countries: [
            { country: 'Brazil' },
            { country: 'Colombia' },
            { country: 'Argentina' }
        ]
    },
    {
        continent: 'Oceania',
        countries: [
            { country: 'Australia' },
            { country: 'New Zealand' },
            { country: 'Samoa' },
        ]
    },
    { continent: 'Antarctica' }
];

//Menu fields definition
let menuFields: FieldSettingsModel = {
    text: ['continent', 'country'],
    children: ['countries']
};

//Initialize Menu component.
let menuObj: Menu = new Menu({ items: data, fields: menuFields }, '#menu');

let insertItem: object[] = [
    {
        continent: 'Europe',
        countries: [
            { country: 'Finland' },
            { country: 'Austria' }
        ]
    }
];

//Add items before to 'Oceania'
menuObj.insertBefore(insertItem, 'Oceania', false);

insertItem = [
    {
        continent: 'Africa',
        countries: [
            { country: 'Nigeria' }
        ]
    }
];

//Add items after to 'Asia'
menuObj.insertAfter(insertItem, 'Asia', false);

//Remove items
menuObj.removeItems(['South America', 'Mexico'], false);

```

{% endtab %}

> To process items with `ID` values, set `isUnique` to `true`.

## Enable or disable menu items

You can enable and disable the menu items using the [`enableItems`](../../api/menu#enableitems) method in Menu. To enable menuItems, set the `enable` property in argument to `true` and vice-versa.

In the following example, the **Directory** header item, **Conferences**, and **Music** sub menu items are disabled.

{% tab template="menu/enable-items", sourceFiles="app.ts,index.html,styles.css",
 es5Template="enable-template", isDefaultActive=true %}

```typescript
import { Menu, MenuItemModel, BeforeOpenCloseMenuEventArgs } from '@syncfusion/ej2-navigations';
import { Button } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//Menu items definition
let menuItems: MenuItemModel[] = [
    {
        text: 'Events',
        items: [
            { text: 'Conferences' },
            { text: 'Music' },
            { text: 'Workshops' }
        ]
    },
    {
        text: 'Movies',
        items: [
            { text: 'Now Showing' },
            { text: 'Coming Soon' }
        ]
    },
    {
        text: 'Directory',
        items: [
            { text: 'Media Gallery' },
            { text: 'Newsletters' }
        ]
    },
    {
        text: 'Queries',
        items: [
            { text: 'Our Policy' },
            { text: 'Site Map' }
        ]
    },
    { text: 'Services' }
];

// Initialize Menu component.
let menuObj: Menu = new Menu({
    items: menuItems,
    beforeOpen: (args: BeforeOpenCloseMenuEventArgs) => {
        //Handling sub menu items
        for (let i: number = 0; i  < args.items.length; i++) {
            if (disableItems.indexOf(args.items[i].text) > -1) {
                menuObj.enableItems([args.items[i].text], false, false);
            }
        }
    }
}, '#menu');

let disableItems: string[] = ['Conferences', 'Music', 'Directory'];

//Disable items
menuObj.enableItems(disableItems, false, false);

let buttonObj: Button = new Button();
buttonObj.appendTo('#enableAll');

buttonObj.element.onclick = (): void => {
    menuObj.enableItems(disableItems, true, false);
    disableItems = [];
}
```

{% endtab %}

> To disable sub menu items, use the [`beforeOpen`](../../api/menu#beforeopen) event.

## Hide or show menu items

You can show or hide the menu items using the [`showItems`](../../api/menu#showitems) and [`hideItems`](../../api/menu#hideitems) methods.

In the following example, the **Movies** header item, **Workshops**, and **Music** sub menu items are hidden in menu.

{% tab template="menu/hide-items", sourceFiles="app.ts,index.html,styles.css",
 es5Template="hide-template", isDefaultActive=true %}

```typescript
import { Menu, MenuItemModel, BeforeOpenCloseMenuEventArgs } from '@syncfusion/ej2-navigations';
import { Button } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//Menu items definition
let menuItems: MenuItemModel[] = [
    {
        text: 'Events',
        items: [
            { text: 'Conferences' },
            { text: 'Music' },
            { text: 'Workshops' }
        ]
    },
    {
        text: 'Movies',
        items: [
            { text: 'Now Showing' },
            { text: 'Coming Soon' }
        ]
    },
    {
        text: 'Directory',
        items: [
            { text: 'Media Gallery' },
            { text: 'Newsletters' }
        ]
    },
    {
        text: 'Queries',
        items: [
            { text: 'Our Policy' },
            { text: 'Site Map' }
        ]
    },
    { text: 'Services' }
];

// Initialize Menu component.
let menuObj: Menu = new Menu({
    items: menuItems,
    beforeOpen: (args: BeforeOpenCloseMenuEventArgs) => {
        //Handling sub menu items
        for (let i: number = 0; i  < args.items.length; i++) {
            if (hiddenItems.indexOf(args.items[i].text) > -1) {
                menuObj.hideItems([args.items[i].text], false);
            }
        }
    },
}, '#menu');

let hiddenItems: string[] = ['Workshops', 'Music', 'Movies'];

//Hide items
menuObj.hideItems(hiddenItems, false);

let buttonObj: Button = new Button();
buttonObj.appendTo('#showAll');

buttonObj.element.onclick = (): void => {
    menuObj.showItems(hiddenItems, false);
    hiddenItems = [];
}
```

{% endtab %}

> Using the [`beforeOpen`](../../api/menu#beforeopen) event, you can hide the sub menu items as in the above example since the menu supports to hide items only for headers initially.