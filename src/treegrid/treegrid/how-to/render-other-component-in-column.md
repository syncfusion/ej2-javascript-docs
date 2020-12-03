---
title: "Render other component in a column"
component: "TreeGrid"
description: "Learn how to Render other component in a column."
---

# Render other component in a column

You can render any components in a Tree Grid column using the template property.

Initialize the column template for your custom component. The template property renders the custom component.

In the following sample, the DropDownList is rendered in the **Priority** column.

{% tab template="treegrid/render-component", sourceFiles="index.ts,index.css,index.html",es5Template="render-component" %}

```typescript

import { TreeGrid, Edit, Toolbar } from "@syncfusion/ej2-treegrid";
import { projectData } from './datasource.ts';
import { DropDownList } from "@syncfusion/ej2-dropdowns";
import { QueryCellInfoEventArgs } from "@syncfusion/ej2-grids";

let dropData = ["Normal", "Low", "High", "Critical", "Breaker"];

let treegrid: TreeGrid = new TreeGrid({
  dataSource: projectData,
  idMapping: "TaskID",
  parentIdMapping: "parentID",
  treeColumnIndex: 1,
  queryCellInfo: dropdown,
  height: 273,
  columns: [
    { field: "TaskID", headerText: "Task ID", textAlign: "Right", width: 70 },
    { field: "TaskName", headerText: "Task Name", width: 100 },
    { field: "StartDate", headerText: "Start Date", textAlign: "Right", width: 100,
      format: { skeleton: "yMd", type: "date" } },
    { field: "EndDate", headerText: "End Date", textAlign: "Right", width: 90,
      format: { skeleton: "yMd", type: "date" } },
    { field: "Duration", headerText: "Duration", textAlign: "Right", width: 90 },
    { headerText: "Priority", width: 90, template: `<input type="text" tabindex="1" id='ddlelement' />` }
  ]
});
treegrid.appendTo("#TreeGrid");
function dropdown(args: QueryCellInfoEventArgs) {
  let ele: HTMLSelectElement = args.cell.querySelector("#ddlelement");
  let drop: DropDownList = new DropDownList({
    dataSource: dropData,
    value: args.data["Priority"],
    popupHeight: 150,
    popupWidth: 150,
    change: valueChange
  });
  drop.appendTo(ele);
}
function valueChange(args) {
  /** Event will trigger when you have change the value in dropdown column */
  alert(args.value);
}

```

{% endtab %}