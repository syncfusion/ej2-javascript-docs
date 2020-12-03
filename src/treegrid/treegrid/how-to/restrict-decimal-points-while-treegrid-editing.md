---
title: "Restrict to type decimal points in a NumericTextBox while editing the numeric column"
component: "TreeGrid"
description: "Learn how restrict to type decimal points in a NumericTextBox while editing the numeric column."
---

# Restrict to type decimal points in a NumericTextBox while editing the numeric column

By default, the number of decimal places will be restricted to two in the NumericTextBox while editing the numeric column. We can restrict to type the decimal points in a NumericTextBox by using the **validateDecimalOnType** and **decimals** properties of NumericTextBox.

In the below demo, while editing the row we have restricted to type the decimal point value in the NumericTextBox of **Price** column.

{% tab template="treegrid/restrict-decimal", sourceFiles="index.ts,index.css,index.html",es5Template="restrict-decimal" %}

```typescript

import { TreeGrid, Edit, Toolbar } from "@syncfusion/ej2-treegrid";
import { stackedData } from './datasource.ts';

TreeGrid.Inject(Edit, Toolbar);

let treegrid: TreeGrid = new TreeGrid({
  dataSource: stackedData,
  childMapping: "subtasks",
  treeColumnIndex: 1,
  height: 265,
  editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
  toolbar: ["Add", "Delete", "Update", "Cancel"],
  columns: [
    { field: "orderID", headerText: "Order ID", textAlign: "Right", isPrimaryKey: true, width: 70 },
    { field: "orderName", headerText: "Order Name", width: 100 },
    { field: "orderDate", headerText: "Order Date", textAlign: "Right", width: 100, editType: "datepickeredit",
      format: { skeleton: "yMd", type: "date" } },
    { field: "shippedDate", headerText: "Shipped Date", textAlign: "Right", width: 100,
      editType: "datepickeredit", format: { skeleton: "yMd", type: "date" } },
    { field: "shipMentCategory", headerText: "Shipment Category", textAlign: "Right", width: 100 },
    { field: "units", headerText: "Units", width: 90, editType: "numericedit" },
    { field: "price", headerText: "Price", width: 90, editType: "numericedit",
      edit: {
        params: {
          validateDecimalOnType: true,
          decimals: 0,
          format: "N"
        }
      }
    }
  ]
});
treegrid.appendTo("#TreeGrid");

```

{% endtab %}