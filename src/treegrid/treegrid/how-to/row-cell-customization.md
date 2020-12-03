---
title: "Row and Cell Customization in Tree Grid"
component: "TreeGrid"
description: "Learn how to customize the row and cell in Tree Grid"
---

# Row and Cell Customization in Tree Grid

In Tree Grid we can customize the row and cell using [`queryCellInfo`](../api/treegrid/#querycellinfo) and [`rowDataBound`](../api/treegrid/#rowdatabound) events of Tree Grid.

In the below demo, we customize and show the command buttons only for the parent rows using [`queryCellInfo`](../api/treegrid/#querycellinfo) and [`rowDataBound`](../api/treegrid/#rowdatabound) events of Tree Grid.

{% tab template="treegrid/custom-row-cell", sourceFiles="index.ts,index.css,index.html",es5Template="custom-row-cell" %}

```typescript

import { TreeGrid, CommandColumn, Column, ITreeData } from "@syncfusion/ej2-treegrid";
import { sampleData } from './datasource.ts';
import { QueryCellInfoEventArgs, RowDataBoundEventArgs } from "@syncfusion/ej2-grids";

TreeGrid.Inject(CommandColumn);

let treegrid: TreeGrid = new TreeGrid({
  dataSource: sampleData,
  childMapping: "subtasks",
  treeColumnIndex: 1,
  height: 280,
  rowDataBound: rowDataBound,
  queryCellInfo: queryCellInfo,
  columns: [
    { field: "taskID", headerText: "Task ID", isPrimaryKey: true, width: 80, textAlign: "Right" },
    { field: "taskName", headerText: "Task Name", width: 200 },
    { field: "startDate", headerText: "Start Date", textAlign: "Right", width: 90,
      format: { skeleton: "yMd", type: "date" } },
    { field: "endDate", headerText: "End Date", textAlign: "Right", width: 90,
      format: { skeleton: "yMd", type: "date" } },
    { field: "duration", headerText: "Duration", textAlign: "Right", width: 90 },
    { field: "progress", headerText: "Progress", width: 90 },
    { headerText: "Commands", width: 120,
      commands: [
        {
          buttonOption: {
            content: "Details",
            cssClass: "e-flat"
          }
        }
      ]
    }
  ]
});
treegrid.appendTo("#TreeGrid");
function rowDataBound(args: RowDataBoundEventArgs) {
  if (!(args.data as ITreeData).hasChildRecords) {
    (args.row as HTMLElement).style.backgroundColor = "green";
  }
}
function queryCellInfo(args: QueryCellInfoEventArgs) {
  if (!(args.data as ITreeData).hasChildRecords) {
    if ((args.cell as HTMLElement).classList.contains("e-unboundcell")) {
      ((args.cell as HTMLElement).querySelector(
        ".e-unboundcelldiv"
      ) as HTMLElement).style.display = "none";
    }
  }
}

```

{% endtab %}