---
title: "Context Menu"
component: "TreeGrid"
description: "Learn how to use the context menu and add custom context menu items in the Essential JS 2 TreeGrid control."
---

# Context menu

The TreeGrid has options to show the context menu when right clicked on it. To enable this feature, you need to define either default or custom item in the [`contextMenuItems`](../api/treegrid/#contextmenuitems).

To use the context menu, inject the `ContextMenu` module in the treegrid.

The default items are in the following table.

Items| Description
----|----
`AutoFit`|  Auto fit the current column.
`AutoFitAll` | Auto fit all columns.
`Edit`|  Edit the current record.
`Delete` | Delete the current record.
`Save` | Save the edited record.
`Cancel` | Cancel the edited state.
`PdfExport` | Export the treegrid data as Pdf document.
`ExcelExport` | Export the treegrid data as Excel document.
`CsvExport` | Export the treegrid data as CSV document.
`SortAscending` | Sort the current column in ascending order.
`SortDescending` | Sort the current column in descending order.
`FirstPage` | Go to the first page.
`PrevPage` | Go to the previous page.
`LastPage` | Go to the last page.
`NextPage` | Go to the next page.
`AddRow` | Add new row to the treegrid.

{% tab template="treegrid/contextmenu", es5Template="contextmenu" %}

```typescript
import { TreeGrid, Resize, Sort, ContextMenu, Edit, Page, PdfExport, ExcelExport } from '@syncfusion/ej2-treegrid';
import { sampleData  } from './datasource.ts';

TreeGrid.Inject(Resize, Sort, Edit, ContextMenu, Page, PdfExport, ExcelExport);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowSorting: true,
    allowResizing: true,
    allowPaging: true,
    pageSettings: {pageSize: 7},
    editSettings: {allowEditing: true, allowAdding: true, allowDeleting: true, mode:"Row"},
    allowPdfExport: true,
    allowExcelExport: true,
    contextMenuItems: ['AutoFit', 'AutoFitAll', 'SortAscending', 'SortDescending','Edit',                     'Delete', 'Save', 'Cancel', 'PdfExport', 'ExcelExport', 'CsvExport'                              'FirstPage', 'PrevPage', 'LastPage', 'NextPage'],
    treeColumnIndex: 1,
    columns: [
                { field: 'taskID', headerText: 'Task ID', isPrimaryKey: true, width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
                {
                    field: 'startDate', headerText: 'Start Date', width: 90, editType: 'datePickeredit', textAlign: 'Right', type: 'date', format: 'yMd'
                },
                { field: 'duration', headerText: 'Duration', width: 80, editType: 'numericedit', textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');


```

{% endtab %}

## Custom context menu items

The custom context menu items can be added by defining the [`contextMenuItems`](../api/treegrid/#contextmenuitems) as a collection of
[`contextMenuItemModel`](../api/grid/contextMenuItemModel/).
Actions for this customized items can be defined in the [`contextMenuClick`](../api/treegrid/#contextmenuclick) event.

In the below sample, we have shown context menu item for parent rows to expand or collapse child rows.

{% tab template="treegrid/contextmenu", es5Template="customcontext" %}

```typescript
import { TreeGrid, ContextMenu, Page } from '@syncfusion/ej2-treegrid';
import { getValue, isNullOrUndefined } from '@syncfusion/ej2-base';
import { sampleData  } from './datasource.ts';
import { BeforeOpenCloseEventArgs } from '@syncfusion/ej2-inputs';
import { MenuEventArgs } from '@syncfusion/ej2-navigations';

TreeGrid.Inject(ContextMenu, Page);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowPaging: true,
    pageSettings: {pageSize: 7},
    contextMenuItems: [
                {text: 'Collapse the Row', target: '.e-content', id: 'collapserow'},
                {text: 'Expand the Row', target: '.e-content', id: 'expandrow'}
            ],
    contextMenuClick: (args?: MenuEventArgs) => {
        treeGridObj.getColumnByField('taskID');
        if (args.item.id === 'collapserow') {
            treeGridObj.collapseRow(<HTMLTableRowElement>(treeGridObj.getSelectedRows()[0]));
        } else {
            treeGridObj.expandRow(<HTMLTableRowElement>(treeGridObj.getSelectedRows()[0]));
        }
    },
    contextMenuOpen: (arg?: BeforeOpenCloseEventArgs) => {
        let elem: Element = arg.event.target as Element;
        let uid: string = elem.closest('.e-row').getAttribute('data-uid');
        if (isNullOrUndefined(getValue('hasChildRecords', treeGridObj.grid.getRowObjectFromUID(uid).data))) {
            arg.cancel = true;
        } else {
            let flag: boolean = getValue('expanded', treeGridObj.grid.getRowObjectFromUID(uid).data);
            let val: string = flag ? 'none' : 'block';
            document.querySelectorAll('li#expandrow')[0].setAttribute('style', 'display: ' + val + ';');
            val = !flag ? 'none' : 'block';
            document.querySelectorAll('li#collapserow')[0].setAttribute('style', 'display: ' + val + ';');
        }
    },
    treeColumnIndex: 1,
    columns: [
                { field: 'taskID', headerText: 'Task ID',  width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
                {
                    field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
                },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');


```

{% endtab %}

> You can hide or show an item in context menu for specific area inside of treegrid by defining the [`target`](../api/grid/contextMenuItemModel/#target) property.