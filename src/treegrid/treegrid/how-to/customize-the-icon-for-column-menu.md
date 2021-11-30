---
title: "Customize the icon for column menu"
component: "TreeGrid"
description: "Learn how to customize the icon for column menu."
---

# Customize the icon for column menu

You can customize the column menu icon by overriding the default Tree Grid class **.e-icons.e-columnmenu** with a custom property **content** as mentioned below,

```css
    .e-treegrid .e-columnheader .e-icons.e-columnmenu::before {
        content: "\e903";
    }
```

In the below sample, Tree Grid is rendered with a customized column menu icon.

{% tab template="treegrid/custom-column-menu-icon", sourceFiles="index.ts,index.css,index.html",es5Template="custom-column-menu-icon" %}

```typescript

import { TreeGrid, ColumnMenu } from "@syncfusion/ej2-treegrid";
import { projectData } from './datasource.ts';

TreeGrid.Inject(ColumnMenu);

let treegrid: TreeGrid = new TreeGrid({
  dataSource: projectData,
  idMapping: "TaskID",
  parentIdMapping: "parentID",
  treeColumnIndex: 1,
  height: 315,
  showColumnMenu: true,
  columns: [
    { field: "TaskID", headerText: "Task ID", textAlign: "Right", width: 70 },
    { field: "TaskName", headerText: "Task Name", width: 100 },
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

> You can refer to our [`JavaScript Tree Grid`](https://www.syncfusion.com/javascript-ui-controls/js-tree-grid) feature tour page for its groundbreaking feature representations. You can also explore our JavaScript Tree Grid example [`JavaScript Tree Grid example`](https://ej2.syncfusion.com/demos/#/material/tree-grid/treegrid-overview.html) to knows how to present and manipulate data.