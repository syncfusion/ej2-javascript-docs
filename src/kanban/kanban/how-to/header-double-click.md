---
title: "Header double click"
component: "Kanban"
description: "This article demonstrates how to bind the double click event on Kanban header cells and how to get the header information."
---

# Add header double click

You can bind the header double click event by using the [`dataBound`](../../api/kanban#dataBound) event at the initial rendering. You can get the column header text when you double click on the headers.

{% tab template="kanban/how-to", es5Template="header-double-click", sourceFiles="index.ts,index.html,datasource.ts" %}

```typescript
import { Kanban } from '@syncfusion/ej2-kanban';
import { DialogUtility } from '@syncfusion/ej2-popups';
import { closest } from '@syncfusion/ej2-base';
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
    dataBound: function () {
        let headerEle: HTMLElement = document.querySelector('.e-header-row');
        headerEle.addEventListener("dblclick", function (e: Event) {
            let target = closest((<HTMLElement>e.target), '.e-header-cells');
            DialogUtility.alert({
                title: 'Header',
                content: "Double clicked on " + (<HTMLElement>target.querySelector('.e-header-text')).innerText + " header",
                showCloseIcon: true,
                closeOnEscape: true,
                animationSettings: { effect: 'Zoom' }
            });
        });
    }
});
kanbanObj.appendTo('#Kanban');
```

{% endtab %}