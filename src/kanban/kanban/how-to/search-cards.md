---
title: "Searching Cards"
component: "Kanban"
description: "This article demonstrates how to show the cards in Kanban board when you type or search the text in the textbox."
---

# Searching Cards

You can search the cards in Kanban by using the `query` property.

In the following sample, the searching operation starts as soon as you start typing characters in the external text box. It will search the cards based on the `Id` and `Summary` using the `search` query with `contains` operator.

{% tab template="kanban/search-cards", es5Template="search-cards", sourceFiles="index.ts,index.html,datasource.ts" %}

```typescript
import { Kanban } from '@syncfusion/ej2-kanban';
import { TextBox } from '@syncfusion/ej2-inputs';
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

let textObj: TextBox = new TextBox({
    placeholder: 'Enter search text',
    showClearButton: true,
    width: 180
});
textObj.appendTo('#search');
document.getElementById('reset').onclick = () => {
    textObj.value = '';
    kanbanObj.query = new Query();
};
document.getElementById('search').onkeyup = (e: KeyboardEvent) => {
    let searchValue: string = (<HTMLInputElement>e.target).value;
    let searchQuery: Query = new Query();
    if (searchValue !== '') {
        searchQuery = new Query().search(searchValue, ['Id', 'Summary'], 'contains', true);
    }
    kanbanObj.query = searchQuery;
};
```

{% endtab %}