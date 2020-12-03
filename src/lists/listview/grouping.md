---
title: "Syncfusion JavaScript ListView Grouping"
component: "ListView"
description: "Learn about JavaScript listview control with grouping, which helps to group the logically related items under a category."
---

# Grouping

The ListView supports to wrap the nested element into a group based on the category. The category of each list item can be mapped with groupBy field in the data table, that also support single-level navigation.

In the following sample, The cars are grouped based on its category by using the groupBy field.

{% tab template="listview/grouping", isDefaultActive = "true", sourceFiles="index.ts,index.html",es5Template="group-template" %}

```typescript

import { ListView } from '@syncfusion/ej2-lists';

//define the array of JSON
let cars: { [key: string]: Object }[] = [
    {
        'text': 'Audi A4',
        'id': '9bdb',
        'category': 'Audi'
    },
    {
        'text': 'Audi A5',
        'id': '4589',
        'category': 'Audi'
    },
    {
        'text': 'Audi A6',
        'id': 'e807',
        'category': 'Audi'
    },
    {
        'text': 'Audi A7',
        'id': 'a0cc',
        'category': 'Audi'
    },
    {
        'text': 'Audi A8',
        'id': '5e26',
        'category': 'Audi'
    },
    {
        'text': 'BMW 501',
        'id': 'f849',
        'category': 'BMW'
    },
    {
        'text': 'BMW 502',
        'id': '7aff',
        'category': 'BMW'
    },
    {
        'text': 'BMW 503',
        'id': 'b1da',
        'category': 'BMW'
    },
    {
        'text': 'BMW 507',
        'id': 'de2f',
        'category': 'BMW'
    },
    {
        'text': 'BMW 3200',
        'id': 'b2b1',
        'category': 'BMW'
    }
];

//Initialize ListView control
let listviewInstance: ListView = new ListView({
    //set the data to datasource property
    dataSource: cars,

    // map the groupBy field with category column
    fields: { groupBy: 'category', tooltip: 'text' }
});

//Render initialized ListView
listviewInstance.appendTo("#element");

```

{% endtab %}

## Customization

The grouping header can be customized by using the groupTemplate property for both inline and fixed group header. The complete customization description and explanation with an example is given in the following link.

[Group Template](./customizing-templates#group-template).
