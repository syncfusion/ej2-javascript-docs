---
title: "Module Injection"
component: "TreeGrid"
description: "Learn what are the feature modules are available in EJ2 TreeGrid."
---

# Module injection

The following feature modules should be injected to extend the TreeGrid's functionality.

| Module | Description |
|------|-------------|
| [`PageService`](../../treegrid/paging)| Inject this module to use paging feature.|
| [`SortService`](../../treegrid/sorting)| Inject this module to use sorting feature.|
| [`FilterService`](../../treegrid/filtering)| Inject this module to use filtering feature.|
| [`EditService`](../../treegrid/edit)| Inject this module to use editing feature.|
| [`AggregateService`](../../treegrid/aggregates)| Inject this module to use aggregate feature.|
| [`ColumnChooserService`](../api/treegrid/columnChooser)| Inject this module to use column chooser feature.|
| [`ColumnMenuService`](../../treegrid/columns/#column-menu)| Inject this module to use column menu feature.|
| [`CommandColumnService`](../../treegrid/edit/#command-column)| Inject this module to use command column feature.|
| [`ContextMenuService`](../../treegrid/context-menu)| Inject this module to use context menu feature.
| [`ResizeService`](../../treegrid/columns/#column-resizing)| Inject this module to use resize feature.|
| [`ReorderService`](../../treegrid/columns/#reorder)| Inject this module to use reorder feature.|
| [`PrintService`](../../treegrid/print)| Inject this module to use to use print feature and this is a default injected module.|
| [`ToolbarService`](../../treegrid/tool-bar)| Inject this module to use toolbar feature.|
| [`ExcelExportService`](../../treegrid/excel-export)| Inject this module to use Excel export feature.|
| [`PdfExportService`](../../treegrid/pdf-export)| Inject this module to use PDF export feature.|

These modules should be injected into the TreeGrid using the `ej.treegrid..TreeGrid.Inject` method.

> You can refer to our [`JavaScript Tree Grid`](https://www.syncfusion.com/javascript-ui-controls/js-tree-grid) feature tour page for its groundbreaking feature representations. You can also explore our JavaScript Tree Grid example [`JavaScript Tree Grid example`](https://ej2.syncfusion.com/demos/#/material/tree-grid/treegrid-overview.html) to knows how to present and manipulate data.
