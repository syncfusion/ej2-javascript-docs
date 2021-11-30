---
title: "Select Tree Grid rows based on certain condition"
component: "TreeGrid"
description: "Learn how to select rows in Tree Grid based on certain condition"
---

# Select Tree Grid rows based on certain condition

You can select the specific row in the Tree Grid based on a certain condition by using the [`selectRows`](../api/treegrid/#selectrows) method in the [`dataBound`](../api/treegrid/#databound) event of Tree Grid.

In the below demo, we have selected the Tree Grid rows only when *Duration* column value greater than *4*.

{% tab template="treegrid/select-rows", sourceFiles="index.ts,index.css,index.html",es5Template="select-rows" %}

```typescript

import { TreeGrid, Page } from "@syncfusion/ej2-treegrid";
import { projectData } from './datasource.ts';
import { RowDataBoundEventArgs } from "@syncfusion/ej2-grids";
import { getValue } from "@syncfusion/ej2-base";

TreeGrid.Inject(Page);
let selIndex = [];

let treegrid: TreeGrid = new TreeGrid({
  dataSource: projectData,
  idMapping: "TaskID",
  parentIdMapping: "parentID",
  treeColumnIndex: 1,
  height: 269,
  allowPaging: true,
  selectionSettings: { type: "Multiple" },
  dataBound: dataBound,
  rowDataBound: rowDataBound,
  columns: [
    { field: "TaskID", headerText: "Task ID", textAlign: "Right", width: 70 },
    { field: "TaskName", headerText: "Task Name", width: 150 },
    { field: "StartDate", headerText: "Start Date", textAlign: "Right", width: 90,
      format: { skeleton: "yMd", type: "date" } },
    { field: "EndDate", headerText: "End Date", textAlign: "Right", width: 90,
      format: { skeleton: "yMd", type: "date" } },
    { field: "Duration", headerText: "Duration", textAlign: "Right", width: 80 },
    { field: "Progress", headerText: "Progress", width: 80, textAlign: "Right" },
    { field: "Priority", headerText: "Priority", width: 90 }
  ]
});
treegrid.appendTo("#TreeGrid");
function dataBound(args) {
  if (this && selIndex.length) {
    this.selectRows(selIndex);
    selIndex = [];
  }
}
function rowDataBound(args: RowDataBoundEventArgs) {
  if (getValue("Duration", args.data as object) > 4) {
    selIndex.push(
      parseInt(
        (args.row as HTMLTableRowElement).getAttribute(
          "aria-rowindex"
        ) as string,
        0
      )
    );
  }
}

```

{% endtab %}

> You can refer to our [`JavaScript Tree Grid`](https://www.syncfusion.com/javascript-ui-controls/js-tree-grid) feature tour page for its groundbreaking feature representations. You can also explore our JavaScript Tree Grid example [`JavaScript Tree Grid example`](https://ej2.syncfusion.com/demos/#/material/tree-grid/treegrid-overview.html) to knows how to present and manipulate data.