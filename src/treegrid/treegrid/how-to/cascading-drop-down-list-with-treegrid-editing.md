---
title: "Cascading DropDownList with Tree Grid editing"
component: "TreeGrid"
description: "Learn how to Cascading DropDownList with TreeGrid editing."
---

# Cascading DropDownList with TreeGrid editing

You can achieve the Cascading DropDownList with Tree Grid Editing by using the Cell Edit Template feature.

In the below demo, Cascading DropDownList rendered for **Priority** and **Duration** column.

{% tab template="treegrid/cascading-dropdown", sourceFiles="index.ts,index.css,index.html",es5Template="cascading-dropdown" %}

```typescript

import { TreeGrid, Edit, Toolbar } from "@syncfusion/ej2-treegrid";
import { projectData } from './datasource.ts';
import { DropDownList } from "@syncfusion/ej2-dropdowns";
import { DataManager, Query } from "@syncfusion/ej2-data";

let priorityData: { [key: string]: Object }[] = [
  { priorityName: "Normal", priorityId: "1" },
  { priorityName: "High", priorityId: "2" }
];
let durationData: { [key: string]: Object }[] = [
  { durationValue: 2, priorityId: "1", durationId: 2 },
  { durationValue: 3, priorityId: "1", durationId: 3 },
  { durationValue: 4, priorityId: "1", durationId: 4 },
  { durationValue: 11, priorityId: "2", durationId: 11 },
  { durationValue: 15, priorityId: "2", durationId: 15 },
  { durationValue: 20, priorityId: "2", durationId: 20 }
];
let priorityElem: HTMLElement;
let priorityObj: DropDownList;

let durationElem: HTMLElement;
let durationObj: DropDownList;

TreeGrid.Inject(Edit, Toolbar);

let treegrid: TreeGrid = new TreeGrid({
  dataSource: projectData,
  idMapping: "TaskID",
  parentIdMapping: "parentID",
  treeColumnIndex: 1,
  height: 273,
  toolbar: ["Add", "Edit", "Delete", "Update", "Cancel"],
  editSettings: {
    allowEditing: true,
    allowAdding: true,
    allowDeleting: true,
    mode: "Row"
  },
  columns: [
    { field: "TaskID", headerText: "Task ID", textAlign: "Right", isPrimaryKey: true, width: 70 },
    { field: "TaskName", headerText: "Task Name", width: 100 },
    { field: "StartDate", headerText: "Start Date", textAlign: "Right", width: 100, editType: "datepickeredit",
      format: { skeleton: "yMd", type: "date" } },
    { field: "EndDate", headerText: "End Date", textAlign: "Right", width: 90, editType: "datepickeredit",
      format: { skeleton: "yMd", type: "date" }
    },
    { field: "Priority", headerText: "Priority", width: 90, editType: "dropdownedit",
      edit: {
        create: () => {
          priorityElem = document.createElement("input");
          return priorityElem;
        },
        read: () => {
          return priorityObj.text;
        },
        destroy: () => {
          priorityObj.destroy();
        },
        write: () => {
          priorityObj = new DropDownList({
            dataSource: new DataManager(priorityData),
            fields: { value: "priorityId", text: "priorityName" },
            change: () => {
              durationObj.enabled = true;
              let tempQuery: Query = new Query().where(
                "priorityId",
                "equal",
                priorityObj.value
              );
              durationObj.query = tempQuery;
              durationObj.text = null;
              durationObj.dataBind();
            },
            placeholder: "Select a priority",
            floatLabelType: "Never"
          });
          priorityObj.appendTo(priorityElem);
        }
      }
    },
    { field: "Duration", headerText: "Duration", textAlign: "Right", editType: "dropdownedit", width: 90,
      edit: {
        create: () => {
          durationElem = document.createElement("input");
          return durationElem;
        },
        read: () => {
          return durationObj.text;
        },
        destroy: () => {
          durationObj.destroy();
        },
        write: () => {
          durationObj = new DropDownList({
            dataSource: new DataManager(durationData),
            fields: { value: "durationId", text: "durationValue" },
            enabled: false,
            placeholder: "Select a duration",
            floatLabelType: "Never"
          });
          durationObj.appendTo(durationElem);
        }
      }
    },
    { field: "Progress", headerText: "Progress", textAlign: "Right", width: 90 }
  ]
});
treegrid.appendTo("#TreeGrid");

```

{% endtab %}

> You can refer to our [`JavaScript Tree Grid`](https://www.syncfusion.com/javascript-ui-controls/js-tree-grid) feature tour page for its groundbreaking feature representations. You can also explore our JavaScript Tree Grid example [`JavaScript Tree Grid example`](https://ej2.syncfusion.com/demos/#/material/tree-grid/treegrid-overview.html) to knows how to present and manipulate data.