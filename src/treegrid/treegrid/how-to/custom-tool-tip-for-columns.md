---
title: "Show tooltip in treegrid"
component: "TreeGrid"
description: "Learn how to show tooltip in treegrid"
---

# How to show ToolTip in Tree Grid

You can show the tooltip content in Tree Grid using [`queryCellInfo`] event of Tree Grid.

In the below demo, hover over the cell shows the tooltip content .

{% tab template="treegrid/tooltip", sourceFiles="index.ts,index.css,index.html",es5Template="tooltip" %}

```typescript
import { TreeGrid, Page,QueryCellInfoEventArgs } from '@syncfusion/ej2-treegrid';
import { Tooltip } from '@syncfusion/ej2-popups';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Page);

    let treegrid: TreeGrid = new TreeGrid(
        {
            dataSource: sampleData,
            childMapping: 'subtasks',
            allowPaging: true,
            queryCellInfo: tooltip,
            pageSettings: {pageSize: 10},
            treeColumnIndex: 1,
            columns: [
                { field: 'taskID', headerText: 'Task ID', width: 70, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 200, textAlign: 'Left' },
                { field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd' },
                { field: 'endDate', headerText: 'End Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd' },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
                { field: 'priority', headerText: 'Priority', width: 90 }
            ]  
        });
    treegrid.appendTo('#TreeGrid');

    function tooltip(args: QueryCellInfoEventArgs): void { // event triggers on every cell render.
    let tooltip: Tooltip = new Tooltip({
        content: args.data[args.column.field].toString() // add Essential JS2 tooltip for every cell.
    }, <HTMLElement>args.cell);
}
```

{% endtab %}