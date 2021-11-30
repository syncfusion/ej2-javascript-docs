---
title: "Exporting the Selected Records"
component: "TreeGrid"
description: "Learn how to Export the Selected data."
---

# Exporting the Selected Records

You can export the selected records data by passing it to [`PdfExportProperties.dataSource`](../../api/grid/pdfExportProperties/) or [`ExcelExportProperties.dataSource`](../../api/grid/excelExportProperties/) property in the [`toolbarClick`](../../api/grid/#toolbarclick) event.

In the below exporting demo, we can get the selected records using [`getSelectedRecords`](../api/treegrid/#getselectedrecords) method and pass the selected data to [`pdfExport`](../api/treegrid/#pdfexport) or [`excelExport`](../api/treegrid/#excelExport) methods using respective export properties..

{% tab template="treegrid/export-selected-data", sourceFiles="index.ts,index.css,index.html",es5Template="export-selected-data" %}

```typescript

import { TreeGrid, Page, Toolbar, PdfExport, ExcelExport } from "@syncfusion/ej2-treegrid";
import { projectData } from './datasource.ts';
import { ClickEventArgs } from "@syncfusion/ej2-navigations";

TreeGrid.Inject(Page, ExcelExport, Toolbar, PdfExport);

let treegrid: TreeGrid = new TreeGrid({
  dataSource: projectData,
  idMapping: "TaskID",
  parentIdMapping: "parentID",
  treeColumnIndex: 1,
  allowPaging: true,
  pageSettings: { pageSize: 5, pageCount: 5 },
  selectionSettings: { type: "Multiple" },
  allowExcelExport: true,
  allowPdfExport: true,
  toolbar: ["PdfExport", "ExcelExport"],
  toolbarClick: toolbarClick,
  columns: [
    { field: "TaskID", headerText: "Task ID", textAlign: "Right", width: 70 },
    { field: "TaskName", headerText: "Task Name", width: 100 },
    { field: "StartDate", headerText: "Start Date", textAlign: "Right", width: 100,
      format: { skeleton: "yMd", type: "date" } },
    { field: "EndDate", headerText: "End Date", textAlign: "Right", width: 100,
      format: { skeleton: "yMd", type: "date" } },
    { field: "Duration", headerText: "Duration", textAlign: "Right", width: 90 },
    { field: "Priority", headerText: "Priority", width: 90 }
  ]
});
treegrid.appendTo("#TreeGrid");
function toolbarClick(args: ClickEventArgs) {
  if (treegrid && args.item.text === "PDF Export") {
    const selectedRecords = treegrid.getSelectedRecords();
    const exportProperties = {
      dataSource: selectedRecords
    };
    treegrid.pdfExport(exportProperties);
  } else if (treegrid && args.item.text === "Excel Export") {
    const selectedRecords = treegrid.getSelectedRecords();
    const exportProperties = {
      dataSource: selectedRecords
    };
    treegrid.excelExport(exportProperties);
  }
}

```

{% endtab %}

> You can refer to our [`JavaScript Tree Grid`](https://www.syncfusion.com/javascript-ui-controls/js-tree-grid) feature tour page for its groundbreaking feature representations. You can also explore our JavaScript Tree Grid example [`JavaScript Tree Grid example`](https://ej2.syncfusion.com/demos/#/material/tree-grid/treegrid-overview.html) to knows how to present and manipulate data.