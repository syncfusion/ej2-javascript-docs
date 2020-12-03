---
title: "Menu with datasource and HTML tags"
component: "Menu"
description: "Typescript Menu supports HTML elements for menu items, databinding with local data source, parent child data, array of JSON data, and remote service with query."
---

# Data source binding and Custom menu items

## Data binding

The Menu supports data source bindings such as array of JavaScript objects that can be structured as either `hierarchical` or `self-referential` data.

### Hierarchical data

The Menu can be populated with hierarchical data source by assigning it to the [`items`](../api/menu/menuItemModel#items) property, and the fields with corresponding keys can be mapped to the [`fields`](../api/menu/fieldSettingsModel) property.

#### JSON data

The Menu can generate its menu items through an array of complex data source by mapping fields from the [`fields`](../api/menu/fieldSettingsModel) property.

{% tab template= "menu/getting-started", sourceFiles="app.ts,index.html,styles.css,datasource.ts",
es5Template="local-template", isDefaultActive=true %}

```typescript
import { Menu, FieldSettingsModel } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';

//Import an array of JSON data from datasource.ts
import { dataSource } from './datasource.ts';

enableRipple(true);

//Menu fields definition
let menuFields: FieldSettingsModel = {
    text: ['continent', 'country', 'language'],
    children: ['countries', 'languages']
};

//Initialize Menu component.
let menuObj: Menu = new Menu({ items: dataSource, fields: menuFields }, '#menu');
```

{% endtab %}

#### Data Service

In application level, remote data binding can be achieved using [`DataManager`](https://ej2.syncfusion.com/documentation/data).
To create Menu, assign `items` property with resultant data from
[`callback`](https://ej2.syncfusion.com/documentation/api/data/deferred/#then) function.

The following example displays five employees' **FirstName** from **Employees** table and **ShipName** details from **Orders** table of the `Northwind` Data Service.

{% tab template= "menu/getting-started", sourceFiles="app.ts,index.html,styles.css",
es5Template="remote-template", isDefaultActive=true %}

```typescript
import { Menu, FieldSettingsModel } from '@syncfusion/ej2-navigations';
import { DataManager, Query, ODataAdaptor, ReturnOption } from '@syncfusion/ej2-data';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

const SERVICE_URI: string = 'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/';

// Menu fields definition.
let menuFields: FieldSettingsModel = {
    text: ['FirstName','ShipName'],
    children: ['Orders']
};

// Getting remote data using DataManager.
new DataManager({ url: SERVICE_URI, adaptor: new ODataAdaptor, crossDomain: true })
.executeQuery(
new Query().from('Employees').take(5).hierarchy(
    new Query()
    .foreignKey('EmployeeID')
    .from('Orders').take(13),
    function() {
        return [1,2,3,4,5]
    }
))
.then((e: ReturnOption) => {
    //Initialize Menu component.
    new Menu({ items: ((<Object[]>e.result) as { [key: string]: Object }[]), fields: menuFields  }, '#menu');
});
```

{% endtab %}

### Self-referential data

Menu can be populated from self-referential data structure that contains array of JSON objects with `parentId` mapping.

In the following example, the **id**, **pId**, and **text** columns from self-referential data have been mapped to the [`itemId`](../../api/menu/fieldSettingsModel/#itemid), [`parentId`](../../api/menu/fieldSettingsModel/#parentid), and [`text`](../../api/menu/fieldSettingsModel/#text) fields, respectively.

{% tab template= "menu/getting-started", sourceFiles="app.ts,index.html,styles.css",
es5Template="referential-template", isDefaultActive=true %}

```typescript
import { Menu, FieldSettingsModel } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//Menu datasource
let data:  { [key: string]: Object }[] = [
    { id: 'parent1', text: 'Events' },
    { id: 'parent2', text: 'Movies' },
    { id: 'parent3', text: 'Directory' },
    { id: 'parent4', text: 'Queries', pId: null },
    { id: 'parent5', text: 'Services', pId: null },

    { id: 'parent6', text: 'Conferences', pId: 'parent1' },
    { id: 'parent7', text: 'Music', pId: 'parent1' },
    { id: 'parent8', text: 'Workshops', pId: 'parent1' },

    { id: 'parent9', text: 'Now Showing', pId: 'parent2' },
    { id: 'parent10', text: 'Coming Soon', pId: 'parent2' },

    { id: 'parent10', text: 'Media Gallery', pId: 'parent3' },
    { id: 'parent11', text: 'Newsletters', pId: 'parent3' },

    { id: 'parent12', text: 'Our Policy', pId: 'parent4' },
    { id: 'parent13', text: 'Site Map', pId: 'parent4' },
    { id: 'parent14', text: 'Pop', pId: 'parent7' },
    { id: 'parent15', text: 'Folk', pId: 'parent7' },
    { id: 'parent16', text: 'Classical', pId: 'parent7' }
];

//Menu fields definition
let menuFields: FieldSettingsModel = {
    itemId:'id',
    text: 'text',
    parentId: 'pId'
};

//Initialize Menu component
let menuObj: Menu = new Menu({ items: data, fields: menuFields }, '#menu');
```

{% endtab %}

### HTML element

The Menu can be initialized using `<UL>` element that contains a collection of `<LI>` elements. A `<LI>` item acts as a menu item of the Menu, and the sub `<UL>` element inside the `<LI>` element acts as a sub menu item of its preceding menu item.

{% tab template= "menu/ul-render", sourceFiles="app.ts,index.html,styles.css",
es5Template="ul-template", isDefaultActive=true %}

```typescript
import { Menu } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//Initialize Menu component.
let menuObj: Menu = new Menu(null, '#menu');
```

{% endtab %}

## Custom menu items

The Menu can be customized using Essential JS2 [Template engine](https://ej2.syncfusion.com/documentation/common/template-engine) to render the elements.

To customize menu items in your application, set your customized template string to the [`template`](../api/menu#template) property. In the following example, the menu has been rendered with customized menu items.

{% tab template= "menu/templates", sourceFiles="app.ts,index.html,styles.css",
es5Template="basic-template", isDefaultActive=true %}

```typescript
import { Menu, FieldSettingsModel } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(false);

//Menu data definition
let data:  { [key: string]: Object }[] = [
    {
        category: 'Products',
        options: [
            { value: 'JavaScript', url: 'javascript' },
            { value: 'Angular', url: 'angular' },
            { value: 'ASP.NET Core', url: 'core' },
            { value: 'ASP.NET MVC', url: 'mvc' }
        ]
    },
    {
        category: 'Services',
        options: [
            {
                support: [
                    { value: 'Application Development', count: '1200+' },
                    { value: 'Maintenance & Support', count: '3700+' },
                    { value: 'Quality Assurance' },
                    { value: 'Cloud Integration', count: '900+' }
                ]
            }
        ]
    },
    {
        category: 'About Us',
        options: [
            {
                about: {
                    value: "We are on a mission to provide world-class best software solutions for web, mobile and desktop platforms. Around 900+ applications are desgined and delivered to our customers to make digital & strengthen their businesses."
                }
            }
        ]
    },
    { category: 'Careers' },
    { category: 'Sign In' }
];

//Menu fields definition
let menuFields: FieldSettingsModel  = {
    text: ['category', 'value'],
    children: ['options']
};

//Menu initialization
let menuObj: Menu = new Menu({
    items: data,
    fields: menuFields,
    template: '#menuTemplate'
}, '#menu');
```

{% endtab %}

>To prevent sub menu closing, set `args.cancel` to `true` in [`beforeClose`](../api/menu#beforeclose) event.

## See Also

* [Render menu with items](./getting-started#getting-started)
