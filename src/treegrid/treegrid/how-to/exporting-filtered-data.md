---
title: "Exporting Filtered Data Only"
component: "TreeGrid"
description: "Learn how to customize the Essential JS 2 Tree Grid."
---

# Exporting Filtered Data Only

You can export the filtered data by defining the resulted data in [`PdfExportProperties.dataSource`](../../api/grid/pdfExportProperties/#datasource) before export.

In the below Pdf exporting demo, We have gotten the filtered data from the filteredResult of Tree Grid filterModule and then defines the resulted data in [`PdfExportProperties.dataSource`](../../api/grid/pdfExportProperties/#datasource) and pass it to [`pdfExport`](../api/treegrid/#pdfexport) method.

{% tab template="treegrid/export-filtered-data", sourceFiles="index.ts,index.css,index.html",es5Template="export-filtered-data" %}

```typescript

import { TreeGrid, Page, Toolbar, PdfExport, Filter } from "@syncfusion/ej2-treegrid";
import { projectData } from './datasource.ts';
import { ClickEventArgs } from "@syncfusion/ej2-navigations";

TreeGrid.Inject(Page, Filter, Toolbar, PdfExport);

let treegrid: TreeGrid = new TreeGrid({
  dataSource: projectData,
  idMapping: "TaskID",
  parentIdMapping: "parentID",
  treeColumnIndex: 1,
  allowPaging: true,
  allowFiltering: true,
  pageSettings: { pageSize: 5, pageCount: 5 },
  allowExcelExport: true,
  allowPdfExport: true,
  toolbar: ["PdfExport"],
  toolbarClick: toolbarClick,
  columns: [
    { field: "TaskID", headerText: "Task ID", textAlign: "Right", width: 70,
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
    let pdfdata;
    pdfdata = treegrid.filterModule.filteredResult;
    const exportProperties = {
      dataSource: pdfdata
    };
    if (treegrid) {
      treegrid.pdfExport(exportProperties);
    }
  }
}

```

{% endtab %}