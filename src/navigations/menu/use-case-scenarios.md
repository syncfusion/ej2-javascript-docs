---
title: "Menu use case scenarios"
component: "Menu"
description: "TypeScript Menu how to section, toolbar menu, mobile menu, custom menu, scrollable menu."
---

# Use case scenarios

## Scrollable menu

The menu component supports horizontal and vertical scrolling to render large menus and submenus in an adaptive way. This can be achieved by enabling the [`enableScrolling`](../api/menu/#enablescrolling) property and by restricting the corresponding menu/submenu size.

{% tab template="menu/scroll", sourceFiles="app.ts,index.html,styles.css",
 es5Template="scroll-template", isDefaultActive=true %}

```typescript
import { Menu, MenuItemModel, BeforeOpenCloseMenuEventArgs, MenuModel } from '@syncfusion/ej2-navigations';
import { enableRipple, closest } from '@syncfusion/ej2-base';

enableRipple(true);

// Menu items definition
let menuItems: MenuItemModel[] = [
        {
            text: 'Appliances',
            items: [
                {
                    text: 'Kitchen',
                    items: [
                        { text: 'Electric Cookers' },
                        { text: 'Coffee Makers' },
                        { text: 'Blenders' },
                        { text: 'Microwave Ovens' }
                    ]
                },
                {
                    text: 'Television',
                    items: [
                        { text: 'Our Exclusive TVs' },
                        { text: 'Smart TVs' },
                        { text: 'Big Screen TVs' }
                    ]
                },
                {
                    text: 'Washing Machine'
                },
                {
                    text: 'Refrigerators'
                },
                {
                    text: 'Air Conditioners',
                    items: [
                        { text: 'Inverter ACs' },
                        { text: 'Split ACs' },
                        { text: 'Window ACs' },
                    ]
                },
                {
                    text: 'Water Purifiers'
                },
                {
                    text: 'Air Purifiers'
                },
                {
                    text: 'Chimneys'
                },
                {
                    text: 'Inverters'
                },
                {
                    text: 'Healthy Living'
                },
                {
                    text: 'Vacuum Cleaners'
                },
                {
                    text: 'Room Heaters'
                },
                {
                    text: 'New Launches'
                }
            ]
        },
        {
            text: 'Accessories',
            items: [
                {
                    text: 'Mobile',
                    items: [
                        { text: 'Headphones' },
                        { text: 'Memory Cards' },
                        { text: 'Power Banks' },
                        { text: 'Mobile Cases' },
                        { text: 'Screen Protectors' }
                    ]
                },
                {
                    text: 'Laptops'
                },
                {
                    text: 'Desktop PC',
                    items: [
                        { text: 'Pendrives' },
                        { text: 'External Hard Disks' },
                        { text: 'Monitors' },
                        { text: 'Keyboards' }
                    ]
                },
                {
                    text: 'Camera',
                    items: [
                        { text: 'Lens' },
                        { text: 'Tripods' }
                    ]
                }
            ]
        },
        {
            text: 'Fashion',
            items: [
                {
                    text: 'Men'
                },
                {
                    text: 'Women'
                }
            ]
        },
        {
            text: 'Home & Living',
            items: [
                {
                    text: 'Furniture'
                },
                {
                    text: 'Decor'
                },
                {
                    text: 'Smart Home Automation'
                },
                {
                    text: 'Dining & Serving'
                }
            ]
        },
        {
            text: 'Entertainment',
            items: [
                {
                    text: 'Televisions'
                },
                {
                    text: 'Home Theatres'
                },
                {
                    text: 'Gaming Laptops'
                }
            ]
        },
        {
            text: 'Contact Us'
        },
        {
            text: 'Help'
        }
    ];

let menuOptions: MenuModel = {
    items: menuItems,
    cssClass: 'e-scrollable-menu',
    enableScrolling: true,
    beforeOpen: (args: BeforeOpenCloseMenuEventArgs): void => {
        // Restricting sub menu wrapper height
        if (args.parentItem.text === 'Appliances') {
            (closest(args.element, '.e-menu-wrapper') as HTMLElement).style.height = '230px';
        }
    }
};

new Menu(menuOptions, '#menu');
```

{% endtab %}

## Menu in toolbar

The following example demonstrates how to integrate Menu with Toolbar component.

{% tab template="menu/toolbar-menu", sourceFiles="app.ts,index.html,styles.css",
es5Template="basic-template" %}

```typescript
import { Toolbar, Menu, MenuItemModel } from '@syncfusion/ej2-navigations';

let menuTemplate: string = '<ul id="menu"></ul>';

//Initialize Toolbar component
let toolbarObj: Toolbar = new Toolbar({
    created: create,
    items: [
        { template: menuTemplate },
        { prefixIcon: 'em-icons e-shopping-cart', align: 'Right' }
    ]
});

//Render initialized Toolbar component
toolbarObj.appendTo('#shoppingtoolbar');

function create(): void {
    let data: { [key: string]: Object }[] = [
        {
            header: 'Events',
            subItems: [
                { text: 'Conferences' },
                { text: 'Music' },
                { text: 'Workshops' }
            ]
        },
        {
            header: 'Movies',
            subItems: [
                { text: 'Now Showing' },
                { text: 'Coming Soon' }
            ]
        },
        {
            header: 'Directory',
            subItems: [
                { text: 'Media Gallery' },
                { text: 'Newsletters' }
            ]
        },
        {
            header: 'Queries',
            subItems: [
                { text: 'Our Policy' },
                { text: 'Site Map'},
                { text: '24x7 Support'}
            ]
        },
        { header: 'Services' }
    ];

    //Menu fields definition
    let menuFields: Object = {
        text: ['header', 'text', 'value'],
        children: ['subItems', 'options']
    };

    //Initialize Menu component
    let menuObj: Menu = new Menu({
        items: data,
        fields: menuFields,
        animationSettings: { effect: 'None' }
    }, '#menu');

    this.refreshOverflow();
}
```

{% endtab %}

## Hamburger menu

The following example demonstrates the use case of menu with Accordion component integrated in SideBar.

{% tab template="menu/sidebar-menu", sourceFiles="app.ts,index.html,styles.css",
es5Template="basic-template", isDefaultActive=true %}

```typescript
import { Sidebar, Accordion, ExpandEventArgs, AccordionClickArgs } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let acrdnObj: Accordion;

// Sidebar Initialization
let defaultSidebar: Sidebar = new Sidebar({ width: '220px', type: 'Over', created: created });
defaultSidebar.appendTo('#default-sidebar');

// Close the Sidebar
document.getElementById('close').onclick = (): void => {
    defaultSidebar.hide();
};

document.getElementById('hamburger').onclick = (): void => {
    defaultSidebar.show();
    acrdnObj.refresh();
};

function created(): void {
    let data: { [key: string]: Object }[] = [
        {
            header: 'Appliances',
            content: '<div id="Appliances_Items"></div>',
            subItems: [
                {
                    header: 'Kitchen',
                    content: '<div id="Appliances_Kitchen_Items"></div>',
                    subItems: [
                        { header: 'Electric Cookers' },
                        { header: 'Coffee Makers' },
                        { header: 'Blenders' },
                    ]
                },
                {
                    header: 'Washing Machine',
                    content: '<div id="Appliances_Washing_Items"></div>',
                    subItems: [
                        { header: 'Fully Automatic' },
                        { header: 'Semi Automatic' }
                    ]
                },
                {
                    header: 'Air Conditioners',
                    content: '<div id="Appliances_Conditioners_Items"></div>',
                    subItems: [
                        { header: 'Inverter ACs' },
                        { header: 'Split ACs' },
                        { header: 'Window ACs' },
                    ]
                }
            ]
        },
        {
            header: 'Accessories',
            content: '<div id="Accessories_Items"></div>',
            subItems: [
                {
                    header: 'Mobile',
                    content: '<div id="Accessories_Mobile_Items"></div>',
                    subItems: [
                        { header: 'Headphones' },
                        { header: 'Memory Cards' },
                        { header: 'Power Banks' }
                    ]
                },
                {
                    header: 'Computer',
                    content: '<div id="Accessories_Computer_Items"></div>',
                    subItems: [
                        { header: 'Pendrives' },
                        { header: 'External Hard Disks' },
                        { header: 'Monitors' }
                    ]
                }
            ]
        },
        {
            header: 'Fashion',
            content: '<div id="Fashion_Items"></div>',
            subItems: [
                { header: 'Men' },
                { header: 'Women' }
            ]
        },
        {
            header: 'Home & Living',
            content: '<div id="Home_Living_Items"></div>',
            subItems: [
                { header: 'Furniture' },
                { header: 'Decor'}
            ]
        },
        {
            header: 'Entertainment',
            content: '<div id="Entertainment_Items"></div>',
            subItems: [
                { header: 'Televisions' },
                { header: 'Home Theatres' },
                { header: 'Gaming Laptops' }
            ]
        }
    ];

    //Initialize Accordion component
    acrdnObj = new Accordion ({
        items: data,
        expanding: expand,
        clicked: clicked
    }, '#accordionMenu');
}

//Expanding Event function for Accordion component.
function expand(e: ExpandEventArgs): void {
    if (e.isExpanded) {
        if (e.element.getElementsByClassName('e-acrdn-content')[0].children[0].classList.contains('e-accordion')) {
            return;
        }
        //Initialize Nested Accordion component
        let nestAcrdn: Accordion = new Accordion({
            items: (<{ subItems: object[] }>e.item).subItems,
            expanding: expand,
            clicked: clicked
        });

        let elemId: string = e.element.getElementsByClassName('e-acrdn-content')[0].children[0].id;
        //Render initialized Nested Accordion component
        nestAcrdn.appendTo('#' + elemId);
    }
}

function clicked(e: AccordionClickArgs): void {
    if (!e.item && !(e.originalEvent.target as HTMLElement).closest('.e-acrdn-item').getElementsByClassName('e-tgl-collapse-icon').length) {
        defaultSidebar.hide();
    }
}
```

{% endtab %}

## Mobile view

The following example demonstrates the use case of Menu in Mobile mode by using ListView component with hamburger.

{% tab template="menu/accordion-menu", sourceFiles="app.ts,index.html,styles.css",
es5Template="basic-template", isDefaultActive=true %}

```typescript
import { enableRipple, AnimationOptions } from '@syncfusion/ej2-base';
import { ListView, SelectEventArgs } from '@syncfusion/ej2-lists';
import { Animation } from '@syncfusion/ej2-base';

enableRipple(true);

let dataSource: { [key: string]: Object }[] = [
    {
        text: 'Appliances',
        id: 'list1',
        child: [
            {
                text: 'Kitchen',
                id: 'list1_1',
                child: [
                    { id: 'list1_1_1', text: 'Electric Cookers' },
                    { id: 'list1_1_2', text: 'Coffee Makers' },
                    { id: 'list1_1_3', text: 'Blenders' },
                ]
            },
            {
                text: 'Washing Machine',
                id: 'list1_2',
                child: [
                    { id: 'list1_2_1', text: 'Fully Automatic' },
                    { id: 'list1_2_2', text: 'Semi Automatic' }
                ]
            },
            {
                text: 'Air Conditioners',
                id: 'list1_3',
                child: [
                    { id: 'list1_3_1', text: 'Inverter ACs' },
                    { id: 'list1_3_2', text: 'Split ACs' },
                    { id: 'list1_3_3', text: 'Window ACs' },
                ]
            }
        ]
    },
    {
        text: 'Accessories',
        id: 'list2',
        child: [
            {
                text: 'Mobile',
                id: 'list2_1',
                child: [
                    { id: 'list2_1_1', text: 'Headphones' },
                    { id: 'list2_1_2', text: 'Memory Cards' },
                    { id: 'list2_1_3', text: 'Power Banks' }
                ]
            },
            {
                text: 'Computer',
                id: 'list2_2',
                child: [
                    { id: 'list2_2_1', text: 'Pendrives' },
                    { id: 'list2_2_2', text: 'External Hard Disks' },
                    { id: 'list2_2_3', text: 'Monitors' }
                ]
            }
        ]
    },
    {
        text: 'Fashion',
        id: 'list3',
        child: [
            { id: 'list3_1', text: 'Men' },
            { id: 'list3_2', text: 'Women' }
        ]
    },
    {
        text: 'Home & Living',
        id: 'list4',
        child: [
            { id: 'list4_1', text: 'Furniture' },
            { id: 'list4_2', text: 'Decor'}
        ]
    },
    {
        text: 'Entertainment',
        id: 'list5',
        child: [
            { id: 'list5_1', text: 'Televisions' },
            { id: 'list5_2', text: 'Home Theatres' },
            { id: 'list5_3', text: 'Gaming Laptops' }
        ]
    }
];

//Initialize ListView component
let listObj: ListView = new ListView({

    //Set defined data to dataSource property
    dataSource: dataSource,

    //Set header title
    headerTitle: 'Menu',

    //Set true to show header title
    showHeader: true,

    select: onSelect
});

//Render initialized ListView component
listObj.appendTo('#listview');

document.getElementById('hamburger').onclick = (): void => {
    let animation: Animation = new Animation({ duration: 500 });
    animation.animate(listObj.element, {
        name: 'SlideDown' ,
        begin: function(args: AnimationOptions) {
            listObj.element.style.display = 'block';
            document.getElementById('close').style.display = 'block';
        }
    });
};

// Close the ListView
document.getElementById('close').onclick = (): void => {
    listObj.element.style.display = 'none';
    document.getElementById('close').style.display = 'none';
};

function onSelect (e: SelectEventArgs): void {
    if (e.data && !(e.data as { child: object }).child) {
        listObj.element.style.display = 'none';
        document.getElementById('close').style.display = 'none';
        listObj.refresh();
    }
}
```

{% endtab %}