---
title: "Customize the Edit Dialog"
component: "TreeGrid"
description: "Learn how to customize the Edit Dialog."
---

# Customize the Edit Dialog

You can customize the appearance of the edit dialog in the [`actionComplete`](../api/treegrid/#actioncomplete) event based on **requestType** as **beginEdit** or **add**.

In the below example, we have changed the dialog's header text for editing and adding records.

{% tab template="treegrid/edit-dialog", sourceFiles="index.ts,index.css,index.html",es5Template="edit-dialog" %}

```typescript

import { TreeGrid, Toolbar, Edit } from "@syncfusion/ej2-treegrid";
import { projectData } from './datasource.ts';
import { DialogEditEventArgs } from "@syncfusion/ej2-grids";
import { Dialog } from "@syncfusion/ej2-popups";

TreeGrid.Inject(Toolbar, Edit);

let treegrid: TreeGrid = new TreeGrid({
  dataSource: projectData,
  idMapping: "TaskID",
  parentIdMapping: "parentID",
  treeColumnIndex: 1,
  height: 250,
  editSettings: {
    allowAdding: true,
    allowEditing: true,
    allowDeleting: true,
    mode: "Dialog"
  },
  toolbar: ["Add", "Edit", "Delete", "Update", "Cancel"],
  actionComplete: actionComplete,
  columns: [
    { field: "TaskID", headerText: "Task ID", isPrimaryKey: true, textAlign: "Right", width: 70 },
    { field: "TaskName", headerText: "Task Name", width: 100 },
    { field: "StartDate", headerText: "Start Date", textAlign: "Right", width: 90, editType: "datepickeredit",
      format: { skeleton: "yMd", type: "date" }, edit: { params: { format: "y/M/d" } } },
    { field: "EndDate", headerText: "End Date", textAlign: "Right", width: 90, editType: "datepickeredit",
      format: { skeleton: "yMd", type: "date" }, edit: { params: { format: "y/M/d" } } },
    { field: "Duration", headerText: "Duration", textAlign: "Right", width: 90 },
    { field: "Priority", headerText: "Priority", width: 90 }
  ]
});
treegrid.appendTo("#TreeGrid");
function actionComplete(args: DialogEditEventArgs) {
  if (args.requestType === "beginEdit" || args.requestType === "add") {
    const dialog = args.dialog as Dialog;
    const TaskName = "TaskName";
    dialog.height = 400;
    // change the header of the dialog
    dialog.header =
      args.requestType === "beginEdit"
        ? "Record of " + args.rowData[TaskName]
        : "New Customer";
  }
}

```

{% endtab %}

> You can refer to our [`JavaScript Tree Grid`](https://www.syncfusion.com/javascript-ui-controls/js-tree-grid) feature tour page for its groundbreaking feature representations. You can also explore our JavaScript Tree Grid example [`JavaScript Tree Grid example`](https://ej2.syncfusion.com/demos/#/material/tree-grid/treegrid-overview.html) to knows how to present and manipulate data.