---
title: "Tooltip of Kanban"
component: "Kanban"
description: "This article demonstrates how to show the tooltip when hovering card elements and also explained how to use template."
---

# Tooltip

The tooltip is used to show the card information when the cursor hover over the card elements using the `enableTooltip` property. Tooltip content is dynamically set based on hovering over the card elements.

> If you wish to show tooltip on Kanban board custom elements, you need to add `e-tooltip-text` class name of a particular element.

## Tooltip template

You can customize the tooltip content with any HTML or CSS element and styling using the `tooltipTemplate` property. In the following demo, the tooltip is customized with HTML elements.

{% tab template="kanban/tooltip-template", es5Template="tooltip-template", sourceFiles="index.ts,index.html,datasource.ts" %}

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
    },
    enableTooltip: true,
    tooltipTemplate: '#tooltipTemplate'
});
kanbanObj.appendTo('#Kanban');
```

{% endtab %}