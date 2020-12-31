---
title: "Filtering Cards"
component: "Kanban"
description: "This article demonstrates how to filter the collection of cards from the data source and display it on the Kanban board."
---

# Filtering Cards

You can filter the collection of cards from the dataSource and display it on the Kanban board by using the [`query`](../../api/kanban/#query) property.

In the below sample, you can filter the cards based on the ‘where’ query and display the filtered data to the Kanban board.

{% tab template="kanban/filter-cards", es5Template="filter-cards", sourceFiles="index.ts,index.html,datasource.ts" %}

```typescript
import { Kanban } from '@syncfusion/ej2-kanban';
import { DropDownList, ChangeEventArgs } from '@syncfusion/ej2-dropdowns';
import { Query } from '@syncfusion/ej2-data';
import { kanbanData } from './datasource.ts';

let kanbanObj: Kanban = new Kanban({
    dataSource: kanbanData,
    keyField: 'Status',
    columns: [
        { headerText: 'Backlog', keyField: 'Open' },
        { headerText: 'In Progress', keyField: 'InProgress' },
        { headerText: 'Testing', keyField: 'Testing' },
        { headerText: 'Done', keyField: 'Close' }
    ],
    cardSettings: {
        contentField: 'Summary',
        headerField: 'Id'
    }
});
kanbanObj.appendTo('#Kanban');

let priorityObj: DropDownList = new DropDownList({
    dataSource: ['None', 'High', 'Normal', 'Low'],
    index: 0,
    placeholder: 'Select a priority',
    width: 100,
    change: change
});
priorityObj.appendTo('#filter');

function change(args: ChangeEventArgs): void {
    let filterQuery: Query = new Query();
    if (args.value !== 'None') {
        filterQuery = new Query().where('Priority', 'equal', args.value);
    }
    (kanbanObj as any).query = filterQuery;
}
```

{% endtab %}