---
title: "Display ForeignKey value at initial rendering in Tree Grid"
component: "TreeGrid"
description: "Learn how to display ForeignKey value at initial rendering in Tree Grid."
---

# Display ForeignKey value at initial rendering in Tree Grid

Since Tree Grid Databinding concept is of hierarchy relationship, we do not provide in-built support for foreignKey datasource.

To display the foreignKey value at initial rendering, we can use the [`queryCellInfo`](../api/treegrid/#querycellinfo) event of the Tree Grid and also by using the [`editType`](../api/treegrid/column/#edittype) and [`columns.edit`](../api/treegrid/column/#edit) properties of Tree Grid Column, we can render Dropdownlist with external or foreign dataSource.

{% tab template="treegrid/foreign-key", sourceFiles="index.ts,index.css,index.html",es5Template="foreign-key" %}

```typescript

import { TreeGrid, Edit, Toolbar, ITreeData } from "@syncfusion/ej2-treegrid";
import { foreignKeyData, dropData } from './datasource.ts';
import { DataManager, Query } from "@syncfusion/ej2-data";
import { QueryCellInfoEventArgs, Column, IEditCell } from "@syncfusion/ej2-grids";

TreeGrid.Inject(Edit,Toolbar);

let treegrid: TreeGrid = new TreeGrid({
  dataSource: foreignKeyData,
  childMapping: "Children",
  treeColumnIndex: 1,
  height: 269,
  editSettings: {
    allowEditing: true,
    allowAdding: true,
    allowDeleting: true,
    mode: "Cell"
  },
  toolbar: ["Add", "Delete", "Update", "Cancel"],
  queryCellInfo: queryCellInfo,
  columns: [
    { field: "EmpID", headerText: "EmpID", textAlign: "Right", isPrimaryKey: true, width: 70 },
    { field: "Name", headerText: "Employee Name", width: 70 },
    { field: "DOB", headerText: "DOB", textAlign: "Right", width: 70, editType: "datepickeredit",
      format: { skeleton: "yMd", type: "date" } },
    { field: "EmployeeID", headerText: "EmployeeID", textAlign: "Right", editType: "dropdownedit",
      edit: {
        params: {
          dataSource: new DataManager(dropData),
          fields: { text: "EmployeeName", value: "EmployeeID" },
          query: new Query()
        }
      },
      width: 70 },
    { field: "Country", headerText: "Country", width: 90, textAlign: "Right" }
  ]
});
treegrid.appendTo("#TreeGrid");
function queryCellInfo(args: QueryCellInfoEventArgs) {
  if ((args.column as Column).field === "EmployeeID") {
    for (var i = 0; i < dropData.length; i++) {
      let data: Object = args.data as Object;
      if (data[(args.column as Column).field] === dropData[i]["EmployeeID"]) {
        (args.cell as HTMLElement).innerText = dropData[i]["EmployeeName"]; // assign the foreignkey field value to the innertext
      }
    }
  }
}

```

{% endtab %}

> You can refer to our [`JavaScript Tree Grid`](https://www.syncfusion.com/javascript-ui-controls/js-tree-grid) feature tour page for its groundbreaking feature representations. You can also explore our JavaScript Tree Grid example [`JavaScript Tree Grid example`](https://ej2.syncfusion.com/demos/#/material/tree-grid/treegrid-overview.html) to knows how to present and manipulate data.