---
title: "Syncfusion JavaScript ListView Checklist"
component: "ListView"
description: "Learn about JavaScript listview control checklist (listview with checkbox) feature which is used to select more than one list item."
---

# Checklist

The ListView supports checkbox in default and group-lists which is used to select multiple items. The checkbox can be enabled by the `showCheckBox` property.

The Checkbox will be useful in the scenario where we need to select multiple options. For Example, In Shipping cart we can be able to select or unselect the desired items before checkout and also it will be useful in selecting multiple items that belongs to the same category using the group list.

{% tab template="listview/todo-list", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css", es5Template="todo-list-template" %}

```typescript

import { ListView } from '@syncfusion/ej2-lists';

    let listData: { [key: string]: Object }[] = [
        {text: 'Do Meditation', id: '1'},
        {text: 'Go Jogging', id: '2'},
        {text: 'Buy Groceries', id: '3'},
        {text: 'Pay Phone bill', id: '4'},
        {text: 'Play Football with your friends', id: '5'},
    ];

    // Initialize the ListView control
    let listObj: ListView = new ListView({

        //Set the defined data to the data source property
        dataSource: listData,

        headerTitle: 'To DO List',
        showHeader: true,

        //Set true to enable CheckBox
        showCheckBox: true
    });

    //Render the initialized ListView control
    listObj.appendTo('#element');

```

{% endtab %}

## Checkbox Position

In ListView the checkbox can be positioned into either `Left` or `Right` side of the list-item text. This can be achieved by `checkBoxPositon` property. By default, checkbox will be positioned to `Left` of list-item text.

{% tab template="listview/checklist", isDefaultActive = "true", sourceFiles="index.ts,index.html,index.css",es5Template="checklist-position-template" %}

```typescript

import { ListView } from '@syncfusion/ej2-lists';

//define the array of JSON
let data: { [key: string]: Object }[] = [
    { text: 'Hennessey Venom', id: 'list-01' },
    { text: 'Bugatti Chiron', id: 'list-02' },
    { text: 'Bugatti Veyron Super Sport', id: 'list-03' },
    { text: 'SSC Ultimate Aero', id: 'list-04' },
    { text: 'Koenigsegg CCR', id: 'list-05' },
    { text: 'McLaren F1', id: 'list-06' },
    { text: 'Aston Martin One- 77', id: 'list-07' },
    { text: 'Jaguar XJ220', id: 'list-08' },
    { text: 'McLaren P1', id: 'list-09' },
    { text: 'Ferrari LaFerrari', id: 'list-10' },
];

//Initialize ListView control
let listviewInstance: ListView = new ListView({
    //Set the data to datasource property
    dataSource: data,

    //Enable checkbox
    showCheckBox: true,

    //Set Checkbox position
    checkBoxPosition: 'Right'
});

//Render initialized ListView
listviewInstance.appendTo("#element");

```

{% endtab %}