---
title: "Customizing Filter Dialog by using additional Parameter"
component: "TreeGrid"
description: "Learn how to customize the filter dialog in Tree Grid by using an additional Parameter."
---

# Customizing Filter Dialog by using an additional Parameter

You can customize the default settings of the components which are used in Menu filter by using params of filter property in column definition.
In the below sample, TaskID and Duration Columns are numeric columns, while opening the filter dialog you can see that NumericTextBox with spin button is displayed to change/set the filter value. Now using the params option we hide the spin button in NumericTextBox for TaskID Column.

{% tab template="treegrid/add-params", sourceFiles="index.ts,index.css,index.html",es5Template="add-params" %}

```typescript

import { TreeGrid, Filter } from "@syncfusion/ej2-treegrid";
import { projectData } from './datasource.ts';

TreeGrid.Inject(Filter);

let treegrid: TreeGrid = new TreeGrid({
  dataSource: projectData,
  idMapping: "TaskID",
  parentIdMapping: "parentID",
  treeColumnIndex: 1,
  height: 273,
  allowFiltering: true,
  filterSettings: { type: "Menu" },
  columns: [
    { field: "TaskID", headerText: "Task ID", textAlign: "Right", width: 70, filter: { params: { showSpinButton: false } } },
    { field: "TaskName", headerText: "Task Name", width: 100 },
    { field: "StartDate", headerText: "Start Date", textAlign: "Right", width: 90, format: { skeleton: "yMd", type: "date" } },
    { field: "EndDate", headerText: "End Date", textAlign: "Right", width: 90, format: { skeleton: "yMd", type: "date" } },
    { field: "Duration", headerText: "Duration", textAlign: "Right", width: 90 },
    { field: "Priority", headerText: "Priority", width: 90 }
  ]
});
treegrid.appendTo("#TreeGrid");

```

{% endtab %}

> You can refer to our [`JavaScript Tree Grid`](https://www.syncfusion.com/javascript-ui-controls/js-tree-grid) feature tour page for its groundbreaking feature representations. You can also explore our JavaScript Tree Grid example [`JavaScript Tree Grid example`](https://ej2.syncfusion.com/demos/#/material/tree-grid/treegrid-overview.html) to knows how to present and manipulate data.