---
title: "ListView how to display items count in group header"
component: "ListView"
description: "ListView how to section, get selected item, dual list, listview filtering, add & remove items from listview, grid layout using listview, listview drag & drop."
---

# How to display items count in group header

The ListView control supports wrapping list items into a group based on the category. The category of each list item can
be mapped with groupBy field of the data source. You can display grouped list items count in the list-header using the group
header template. Refer to the following code sample to display grouped list item count.

{% tab template="listview/item-count", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css", es5Template="item-template" %}

```typescript

import { ListView } from '@syncfusion/ej2-lists';

let template: string = '<div class="e-list-wrapper e-list-multi-line e-list-avatar">' +
    '<img class="e-avatar e-avatar-circle" src=${image} style="background:#BCBCBC" />' +
    '<span class="e-list-item-header">${Name}</span>' +
    '<span class="e-list-content">${contact}</span>' +
    '</div>';

//Define an array of JSON data
let dataSource: { [key: string]: string }[] = [
    { Name: 'Nancy', contact: '(206) 555-985774', id: '1', image: 'https://ej2.syncfusion.com/demos/src/grid/images/1.png', category: 'Experience' },
    { Name: 'Janet', contact: '(206) 555-3412', id: '2', image: 'https://ej2.syncfusion.com/demos/src/grid/images/3.png', category: 'Fresher' },
    { Name: 'Margaret', contact: '(206) 555-8122', id: '4', image: 'https://ej2.syncfusion.com/demos/src/grid/images/4.png', category: 'Experience' },
    { Name: 'Andrew ', contact: '(206) 555-9482', id: '5', image: 'https://ej2.syncfusion.com/demos/src/grid/images/2.png', category: 'Experience' },
    { Name: 'Steven', contact: '(71) 555-4848', id: '6', image: 'https://ej2.syncfusion.com/demos/src/grid/images/5.png', category: 'Fresher' },
    { Name: 'Michael', contact: '(71) 555-7773', id: '7', image: 'https://ej2.syncfusion.com/demos/src/grid/images/6.png', category: 'Experience' },
    { Name: 'Robert', contact: '(71) 555-5598', id: '8', image: 'https://ej2.syncfusion.com/demos/src/grid/images/7.png', category: 'Fresher' },
    { Name: 'Laura', contact: '(206) 555-1189', id: '9', image: 'https://ej2.syncfusion.com/demos/src/grid/images/8.png', category: 'Experience' },
];

// Initialize the ListView control
let listObj: ListView = new ListView({

    //Set the defined data to the data source property
    dataSource: dataSource,

    //Map the appropriate columns to the fields property
    fields: { text: 'Name', groupBy: 'category' },

    //set cssClass for template customization
    cssClass: 'e-list-template',

    //Set the customized template
    template: template,
    groupTemplate: '<div><span class="category">${items[0].category}</span> <span class="count"> ${items.length} Item(s)</span></div> '

});

//Render the initialized ListView control
listObj.appendTo('#List');

```

{% endtab %}
