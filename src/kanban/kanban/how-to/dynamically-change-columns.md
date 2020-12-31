---
title: "Dynamically change Kanban columns"
component: "Kanban"
description: "This article demonstrates how to dynamically change the particular column or complete column in the Kanban board."
---

# Change Kanban columns dynamically

You can dynamically change the Kanban columns by using the [`columns`](../../api/kanban#columns) property.

In the below sample, you can dynamically change the [`allowToggle`](../../api/kanban/columnsModel/#allowtoggle) property at the particular column when you click on the button. You can also change the initially created columns to the new Kanban columns by using the [`columns`](../../api/kanban#columns) property when you click on the button.

{% tab template="kanban/dynamic-columns", es5Template="dynamic-columns", sourceFiles="index.ts,index.html,datasource.ts" %}

```typescript
import { Kanban } from '@syncfusion/ej2-kanban';
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

let particularColumn: HTMLElement = document.getElementById('particularColumn');
let column: HTMLElement = document.getElementById('column');
particularColumn.onclick = () => {
    kanbanObj.columns[1].allowToggle= true;
};
column.onclick = () => {
    kanbanObj.columns = [
        { headerText: 'To Do', keyField: 'Open' },
        { headerText: 'Done', keyField: 'Close' }
    ]
};
```

{% endtab %}