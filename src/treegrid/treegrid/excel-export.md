---
title: "Migration"
component: "TreeGrid"
description: Documentation on exporting TreeGrid content to Excel document and customizing the exported document with headers and footers, and file name changes."
---

# Excel Export

The excel export allows exporting TreeGrid data to Excel document. You need to use the
 [`excelExport`](../api/treegrid/#excelexport) method for exporting. To enable Excel export in the treegrid, set the [`allowExcelExport`](../api/treegrid/#allowexcelexport-boolean) as true.

To use excel export, You need to inject the `ExcelExport` module in treegrid.

{% tab template="treegrid/excel-export",es5Template="excelexport" %}

```typescript

import { TreeGrid, Toolbar, ExcelExport, Page } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';
TreeGrid.Inject(Toolbar, ExcelExport, Page);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowExcelExport: true,
    allowPaging: true,
    height: 220,
    pageSettings: {pageSize: 7},
    toolbar: ['ExcelExport'],
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});
treeGridObj.toolbarClick = (args: Object) => {
    if (args['item'].text === 'Excel Export') {
        treeGridObj.excelExport();
    }
}
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## To customize excel export

The excel export provides an option to customize mapping of the treegrid to excel document.

### Export hidden columns

The excel export provides an option to export hidden columns of treegrid by defining `includeHiddenColumn` as `true`.

{% tab template="treegrid/excel-export",es5Template="exporthide" %}

```typescript

import { TreeGrid, Toolbar, ExcelExport, Page, ExcelExportProperties } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';
TreeGrid.Inject(Toolbar, ExcelExport, Page);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowExcelExport: true,
    allowPaging: true,
    height: 220,
    pageSettings: {pageSize: 7},
    toolbar: ['ExcelExport'],
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', visible: false, width: 80, textAlign: 'Right' }
    ]
});
treeGridObj.toolbarClick = (args: Object) => {
    if (args['item'].text === 'Excel Export') {
        let excelExportProperties: ExcelExportProperties = {
            includeHiddenColumn: true
        };
        treeGridObj.excelExport(excelExportProperties);
    }
}
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

### Show or Hide columns on Exported Excel

You can show a hidden column or hide a visible column while printing the treegrid using [`toolbarClick`](../api/treegrid#toolbarclick) and [`excelExportComplete`](../api/treegrid/#excelExportComplete) events.

In the `toolbarClick` event, based on `args.item.text` as `Excel Export`. We can show or hide columns by setting `column.visible` property to `true` or `false` respectively.

In the excelExportComplete event, We have reversed the state back to the previous state.

In the below example, we have `Duration` as a hidden column in the treegrid. While exporting, we have changed `Duration` to visible column and `StartDate` as hidden column.

{% tab template="treegrid/excel-export",es5Template="show-hide-excel" %}

```typescript

import { TreeGrid, Page, Toolbar, ExcelExport, ExcelExportProperties } from '@syncfusion/ej2-treegrid';
import { Column }  from '@syncfusion/ej2-grids';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Page, Toolbar, ExcelExport);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowExcelExport: true,
    allowPaging: true,
    height: 220,
    pageSettings: {pageSize: 7},
    toolbar: ['ExcelExport'],
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', visible: false, width: 80, textAlign: 'Right' }
    ]
});
treeGridObj.toolbarClick = (args: Object) => {
if (args['item'].text === 'Excel Export') {
        let cols: Column[] = treeGridObj.grid.columns;
        cols[2].visible = false;
        cols[3].visible = true;
        treeGridObj.excelExport();
    }
}
treeGridObj.excelExportComplete = () => {
    let cols: Column[] = treeGridObj.grid.columns;
    cols[3].visible = false;
    cols[2].visible = true;
}
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

### Conditional Cell Formatting

TreeGrid cells in the exported Excel can be customized or formatted using [`excelQueryCellInfo`](../api/treegrid/#excelQueryCellInfo) event. In this event, we can format the treegrid cells of exported PDF document based on the column cell value.

In the below sample, we have set the background color for `Duration` column in the exported excel by `args.cell` and `backgroundColor` property.

{% tab template="treegrid/excel-export",es5Template="cell-format-excel" %}

```typescript

import { TreeGrid, Page, Toolbar, ExcelExport, ExcelExportProperties, RowDataBoundEventArgs, ExcelQueryCellInfoEventArgs } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Page, Toolbar, ExcelExport);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowExcelExport: true,
    allowPaging: true,
    height: 220,
    pageSettings: {pageSize: 7},
    toolbar: ['ExcelExport'],
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});
treeGridObj.toolbarClick = (args: Object) => {
if (args['item'].text === 'Excel Export') {
        treeGridObj.excelExport();
    }
}
treeGridObj.excelQueryCellInfo = (args: ExcelQueryCellInfoEventArgs) => {
    if(args.column.field == 'duration'){
        if(args.value === 0 || args.value === "") {
            args.style = {backColor: '#336c12'};
        }
        else if(args.value < 3) {
            args.style = {backColor: '#7b2b1d'};
        }
    }
}
treeGridObj.queryCellInfo = (args: RowDataBoundEventArgs) => {
    if (args.data['duration'] == 0 && args.column.field === 'duration' ) {
        args.cell.style.background= '#336c12';
    } else if (args.data['duration'] < 3 && args.column.field === 'duration') {
        args.cell.style.background= '#7b2b1d';
    }
}
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

### Theme

The excel export provides an option to include theme for exported excel document.

To apply theme in exported Excel, define the `theme` in `exportProperties` .

{% tab template="treegrid/excel-export",es5Template="exceltheme" %}

```typescript

import { TreeGrid, Page, Toolbar, ExcelExportProperties, ExcelExport } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Page, Toolbar, ExcelExport);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowExcelExport: true,
    allowPaging: true,
    height: 220,
    pageSettings: {pageSize: 7},
    toolbar: ['ExcelExport'],
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');
treeGridObj.toolbarClick = (args: Object) => {
if (args['item'].text === 'Excel Export') {
        let exportProperties: ExcelExportProperties = {
            theme:
                {
                    header: { fontName: 'Segoe UI', fontColor: '#666666' },
                    record: { fontName: 'Segoe UI', fontColor: '#666666' },
                    caption: { fontName: 'Segoe UI', fontColor: '#666666' }
                }
        };
        treeGridObj.excelExport(exportProperties);
    }
}

```

{% endtab %}

>By default, material theme is applied to exported excel document.

### To add header and footer

The excel export provides an option to include header and footer content for exported excel document.

{% tab template="treegrid/excel-export",es5Template="exportfooter" %}

```typescript

import { TreeGrid, Toolbar, ExcelExport, ExcelExportProperties, Page } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Toolbar, ExcelExport, Page);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowExcelExport: true,
    allowPaging: true,
    height: 220,
    pageSettings: {pageSize: 7},
    toolbar: ['ExcelExport'],
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});
treeGridObj.toolbarClick = (args: Object) => {
    if (args['item'].text === 'Excel Export') {
        let excelExportProperties: ExcelExportProperties = {
            header: {
                headerRows: 7,
                rows: [
                    { cells: [{ colSpan: 4, value: "Northwind Traders", style: { fontColor: '#C67878', fontSize: 20, hAlign: 'Center', bold: true, } }] },
                    { cells: [{ colSpan: 4, value: "2501 Aerial Center Parkway", style: { fontColor: '#C67878', fontSize: 15, hAlign: 'Center', bold: true, } }] },
                    { cells: [{ colSpan: 4, value: "Suite 200 Morrisville, NC 27560 USA", style: { fontColor: '#C67878', fontSize: 15, hAlign: 'Center', bold: true, } }] },
                    { cells: [{ colSpan: 4, value: "Tel +1 888.936.8638 Fax +1 919.573.0306", style: { fontColor: '#C67878', fontSize: 15, hAlign: 'Center', bold: true, } }] },
                    { cells: [{ colSpan: 4, hyperlink: { target: 'https://www.northwind.com/', displayText: 'www.northwind.com' }, style: { hAlign: 'Center' } }] },
                    { cells: [{ colSpan: 4, hyperlink: { target: 'mailto:support@northwind.com' }, style: { hAlign: 'Center' } }] },
                ]
            },
            footer: {
                footerRows: 4,
                rows: [
                    { cells: [{ colSpan: 4, value: "Thank you for your business!", style: { hAlign: 'Center', bold: true } }] },
                    { cells: [{ colSpan: 4, value: "!Visit Again!", style: { hAlign: 'Center', bold: true } }] }
                ]
            },
        };

        treeGridObj.excelExport(excelExportProperties);

    }
}
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

### File Name for Exported document

You can assign the file name for the exported document by defining `fileName` property in [`ExcelExportProperties`](../api/treegrid/#excelExportProperties).

{% tab template="treegrid/excel-export",es5Template="exportfilename" %}

```typescript

import { TreeGrid, Toolbar, ExcelExport, ExcelExportProperties, Page } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Toolbar, ExcelExport, Page);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowExcelExport: true,
    allowPaging: true,
    height: 220,
    pageSettings: {pageSize: 7},
    toolbar: ['ExcelExport'],
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});
treeGridObj.toolbarClick = (args: Object) => {
    if (args['item'].text === 'Excel Export') {
        let excelExportProperties: ExcelExportProperties = {
            fileName:"new.xlsx"
        };
        treeGridObj.excelExport(excelExportProperties);

    }
}
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

### To persist collapsed state

You can persist the collapsed state in the exported document by defining `isCollapsedStatePersist` property as true in `TreeGridExcelExportProperties` parameter of  [`excelExport`](../api/treegrid/#excelexport) method.

{% tab template="treegrid/excel-export",es5Template="exportiscollapsed" %}

```typescript

import { TreeGrid, Toolbar, ExcelExport, TreeGridExcelExportProperties, Page } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Toolbar, ExcelExport, Page);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowExcelExport: true,
    allowPaging: true,
    height: 220,
    pageSettings: {pageSize: 7},
    toolbar: ['ExcelExport'],
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});
treeGridObj.toolbarClick = (args: Object) => {
    if (args['item'].text === 'Excel Export') {
        let excelExportProperties: TreeGridExcelExportProperties = {
            isCollapsedStatePersist: true
        };
        treeGridObj.excelExport(excelExportProperties);
    }
}
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Custom data source

The excel export provides an option to define datasource dynamically before exporting. To export data dynamically, define the `dataSource` in `exportProperties`.

{% tab template="treegrid/excel-export",es5Template="exportdata"  %}

```typescript

import { TreeGrid, Toolbar, ExcelExport, ExcelExportProperties, Page } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Toolbar, ExcelExport, Page);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowExcelExport: true,
    allowPaging: true,
    height: 220,
    pageSettings: {pageSize: 7},
    toolbar: ['ExcelExport'],
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});
treeGridObj.toolbarClick = (args: Object) => {
    if (args['item'].text === 'Excel Export') {
        let excelExportProperties: ExcelExportProperties = {
            dataSource: sampleData
        };
        treeGridObj.excelExport(excelExportProperties);
    }
}
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

> You can refer to our [`JavaScript Tree Grid`](https://www.syncfusion.com/javascript-ui-controls/js-tree-grid) feature tour page for its groundbreaking feature representations. You can also explore our JavaScript Tree Grid example [`JavaScript Tree Grid example`](https://ej2.syncfusion.com/demos/#/material/tree-grid/treegrid-overview.html) to knows how to present and manipulate data.