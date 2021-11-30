---
title: "Show Spinner on TreeGrid when Exporting"
component: "TreeGrid"
description: "Learn how to Show spinner while exporting the Tree Grid."
---

# Show Spinner on TreeGrid when Exporting

You can show/ hide spinner component while exporting the Tree Grid using [`showSpinner`](../api/treegrid/#showspinner)/ [`hideSpinner`](../api/treegrid/#hidespinner) methods. You can use  [`toolbarClick`](../api/treegrid/#toolbarclick) event to show spinner before exporting and hide a spinner in the [`pdfExportComplete`](../api/treegrid/#pdfexportcomplete) or [`excelExportComplete`](../api/treegrid/#excelexportcomplete) event after the exporting.

In the [`toolbarClick`](../../api/grid/#toolbarclick) event, based on the parameter **args.item.text** as **PDF Export** or **Excel Export** we can call the [`showSpinner`](../api/treegrid/#showspinner) method from Tree Grid instance.

In the [`pdfExportComplete`](../api/treegrid/#pdfexportcomplete) or [`excelExportComplete`](../api/treegrid/#excelexportcomplete) event, We can call the [`hideSpinner`](../api/treegrid/#hidespinner) method.

In the below demo, we have rendered the default spinner component when exporting the Tree Grid.

{% tab template="treegrid/show-spinner", sourceFiles="index.ts,index.css,index.html",es5Template="show-spinner" %}

```typescript

import { TreeGrid, Page, Toolbar, PdfExport, ExcelExport } from "@syncfusion/ej2-treegrid";
import { projectData } from './datasource.ts';
import { ClickEventArgs } from "@syncfusion/ej2-navigations";
import { Query } from "@syncfusion/ej2-data";

TreeGrid.Inject(Page, ExcelExport, Toolbar, PdfExport);

let treegrid: TreeGrid = new TreeGrid({
  dataSource: projectData,
  idMapping: "TaskID",
  parentIdMapping: "parentID",
  treeColumnIndex: 1,
  allowPaging: true,
  pageSettings: { pageSize: 5, pageCount: 5 },
  allowExcelExport: true,
  allowPdfExport: true,
  pdfExportComplete: pdfExportComplete,
  excelExportComplete: excelExportComplete,
  toolbar: ["PdfExport", "ExcelExport"],
  toolbarClick: toolbarClick,
  columns: [
    { field: "TaskID", headerText: "Task ID", textAlign: "Right", width: 70 },
    { field: "TaskName", headerText: "Task Name", width: 150 },
    { field: "StartDate", headerText: "Start Date", textAlign: "Right", width: 90,
      format: { skeleton: "yMd", type: "date" } },
    { field: "EndDate", headerText: "End Date", textAlign: "Right", width: 90,
      format: { skeleton: "yMd", type: "date" } },
    { field: "Duration", headerText: "Duration", textAlign: "Right", width: 80 },
    { field: "Priority", headerText: "Priority", width: 90 }
  ]
});
treegrid.appendTo("#TreeGrid");
function toolbarClick(args: ClickEventArgs) {
  if (treegrid && args.item.text === "PDF Export") {
    treegrid.showSpinner();
    treegrid.pdfExport();
  } else if (treegrid && args.item.text === "Excel Export") {
    treegrid.showSpinner();
    treegrid.excelExport();
  }
}
function pdfExportComplete(args) {
  if (treegrid) {
    treegrid.hideSpinner();
  }
}
function excelExportComplete(args) {
  if (treegrid) {
    treegrid.hideSpinner();
  }
}

```

{% endtab %}

> You can refer to our [`JavaScript Tree Grid`](https://www.syncfusion.com/javascript-ui-controls/js-tree-grid) feature tour page for its groundbreaking feature representations. You can also explore our JavaScript Tree Grid example [`JavaScript Tree Grid example`](https://ej2.syncfusion.com/demos/#/material/tree-grid/treegrid-overview.html) to knows how to present and manipulate data.