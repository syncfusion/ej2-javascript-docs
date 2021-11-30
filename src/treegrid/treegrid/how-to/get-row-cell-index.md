---
title: "Get specific row and cell index in Tree Grid"
component: "TreeGrid"
description: "Learn how to get specific row and cell index in Tree Grid."
---

# Get specific row and cell index in Tree Grid

You can get the specific row and cell index of the Tree Grid by using [`rowSelected`](../api/treegrid/#rowselected) event of the treegrid. Here, we can get the row and cell index by using *aria-rowindex* (get row Index from *tr* element) and *aria-colindex* (column index from *td* element) attribute.

{% tab template="treegrid/row-cell-index", sourceFiles="index.ts,index.css,index.html",es5Template="row-cell-index" %}

```typescript

import { TreeGrid } from "@syncfusion/ej2-treegrid";
import { projectData } from './datasource.ts';
import { RowSelectEventArgs } from "@syncfusion/ej2-grids";

let treegrid: TreeGrid = new TreeGrid({
  dataSource: projectData,
  idMapping: "TaskID",
  parentIdMapping: "parentID",
  treeColumnIndex: 1,
  height: 267,
  rowSelected: rowSelected,
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
function rowSelected(args: RowSelectEventArgs) {
  alert("row index: " + " " + (args.row as HTMLTableRowElement).getAttribute("aria-rowindex"));
  alert("column index: " + " " + args.target.closest("td").getAttribute("aria-colindex"));
}

```

{% endtab %}

> You can refer to our [`JavaScript Tree Grid`](https://www.syncfusion.com/javascript-ui-controls/js-tree-grid) feature tour page for its groundbreaking feature representations. You can also explore our JavaScript Tree Grid example [`JavaScript Tree Grid example`](https://ej2.syncfusion.com/demos/#/material/tree-grid/treegrid-overview.html) to knows how to present and manipulate data.