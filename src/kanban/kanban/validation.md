---
title: "WIP validation of Kanban"
component: "Kanban"
description: "This article demonstrates how to set the column or cell validation on Kanban board based on total card count."
---

# Validation

Validate particular column using the `minCount` or `maxCount` properties. The corresponding columns gets different appearance when validation fails. In default layout, `constraintType` property accept only `Column` type. In swimlane layout, accept both `Column` and `Swimlane` constraint type.

There are two types of constraints:
1. Column
2. Swimlane

> By default, the column count validation is performed based on Kanban **columns**.

## Minimum card limit

The `minCount` property is used to specify the minimum cards hold on particular column or swimlane cell. If the column or swimlane total card count falls short of the minimum count value, it shows the column or cell background colour with validation fails.

## Maximum card limit

The `maxCount` property is used to specify the maximum cards hold on particular column or swimlane cell. If the column or swimlane cell total card count exceeds the maximum count value, it shows the column or cell background colour with validation fails.

{% tab template="kanban/column-validation", es5Template="column-validation", sourceFiles="index.ts,index.html,datasource.ts" %}

```typescript
import { Kanban } from '@syncfusion/ej2-kanban';
import { kanbanData } from './datasource.ts';

let kanbanObj: Kanban = new Kanban({
    dataSource: kanbanData,
    keyField: 'Status',
    columns: [
        { headerText: 'Backlog', keyField: 'Open', showItemCount: true, minCount: 6 },
        { headerText: 'In Progress', keyField: 'InProgress', showItemCount: true, maxCount: 5 },
        { headerText: 'Testing', keyField: 'Testing', showItemCount: true, maxCount: 4, minCount: 3 },
        { headerText: 'Done', keyField: 'Close', showItemCount: true }
    ],
    cardSettings: {
        contentField: 'Summary',
        headerField: 'Id'
    }
});
kanbanObj.appendTo('#Kanban');
```

{% endtab %}