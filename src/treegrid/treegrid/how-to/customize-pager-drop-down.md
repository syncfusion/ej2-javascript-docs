---
title: "Customize Pager DropDown"
component: "TreeGrid"
description: "Learn how to Customize Pager DropDown."
---

# Customize Pager DropDown

To customize default values of pager dropdown, you need to define [`pageSizes`](https://ej2.syncfusion.com/angular/documentation/api/treegrid/pageSettings/#pagesizes) as array of strings.

{% tab template="treegrid/pager-dropdown", sourceFiles="index.ts,index.css,index.html",es5Template="pager-dropdown" %}

```typescript

import { TreeGrid, Page } from "@syncfusion/ej2-treegrid";
import { projectData } from './datasource.ts';

TreeGrid.Inject(Page);

let treegrid: TreeGrid = new TreeGrid({
  dataSource: projectData,
  idMapping: "TaskID",
  parentIdMapping: "parentID",
  treeColumnIndex: 1,
  height: 260,
  allowPaging: true,
  pageSettings: { pageSizes: ["5", "10", "All"] },
  columns: [
    { field: "TaskID", headerText: "Task ID", textAlign: "Right", width: 70 },
    { field: "TaskName", headerText: "Task Name", width: 200 },
    { field: "StartDate", headerText: "Start Date", textAlign: "Right", width: 90,
      format: { skeleton: "yMd", type: "date" } },
    { field: "EndDate", headerText: "End Date", textAlign: "Right", width: 90,
      format: { skeleton: "yMd", type: "date" } },
    { field: "Duration", headerText: "Duration", textAlign: "Right", width: 90 },
    { field: "Priority", headerText: "Priority", width: 90 }
  ]
});
treegrid.appendTo("#TreeGrid");

```

{% endtab %}