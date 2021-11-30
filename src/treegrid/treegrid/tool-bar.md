---
title: "ToolBar"
component: "TreeGrid"
description: "Learn how to use the toolbar and add custom toolbar items in the Essential JS 2 TreeGrid control."
---

# ToolBar

The TreeGrid provides ToolBar support to handle treegrid actions. The [`toolbar`](../api/treegrid/#toolbar)
property accepts either the collection of built-in toolbar items and [`ItemModel`](../api/toolbar/#item) objects for custom toolbar items or
HTML element ID for toolbar template.

To use ToolBar, inject `Toolbar` module in the treegrid.

## Built-in toolbar items

Built-in toolbar items execute standard actions of the treegrid, and it can be added by defining the [`toolbar`](../api/treegrid/#toolbar)
as a collection of built-in items. It renders the button with icon and text.

The following table shows built-in toolbar items and its actions.

| Built-in Toolbar Items | Actions |
|------------------------|---------|
| ExpandAll | Expands all the rows.|
| CollapseAll | Collapses all the rows.|
| Add | Adds a new record.|
| Edit | Edits the selected record.|
| Update | Updates the edited record.|
| Delete | Deletes the selected record.|
| Cancel | Cancels the edit state.|
| Search | Searches the records by the given key.|
| Print | Prints the treegrid.|
| ExcelExport | Exports the treegrid to Excel.|
| PdfExport | Exports the treegrid to PDF.|
| WordExport | Exports the treegrid to Word.|

{% tab template="treegrid/toolbar", es5Template="toolbar" %}

```typescript
import { TreeGrid, Toolbar, Filter } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Toolbar, Filter);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    toolbar: ['Print', 'Search'],
    height: 265,
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

```

{% endtab %}

> * The [`toolbar`](../api/treegrid/#toolbar) has options to define both built-in and custom toolbar items.

## Custom toolbar items

Custom toolbar items can be added by defining the [`toolbar`](../api/treegrid/#toolbar) as a collection of
[`ItemModels`](../api/toolbar/#item).
Actions for this customized toolbar items are defined in the [`toolbarClick`](../api/treegrid/#toolbarclick) event.

By default, Custom toolbar items are in position `Left`. You can change the position by using the [`align`](../api/toolbar/#item) property. In the below sample, we have applied position `Right` for the `Quick Filter` toolbar item.

{% tab template="treegrid/toolbar", sourceFiles="index.ts", es5Template="customitems" %}

```typescript
import { TreeGrid, Toolbar, Filter } from '@syncfusion/ej2-treegrid';
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Toolbar, Filter);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    toolbar: [{text: 'Quick Filter', tooltipText: 'Quick Filter', id: 'toolbarfilter', align:'Right'}],
    toolbarClick: (args: ClickEventArgs) => {
        if (args.item.id === 'toolbarfilter') {
            treeGridObj.filterByColumn('taskName', 'startswith', 'Testing');
        }
    },
    allowFiltering: true,
    height: 220,
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

```

{% endtab %}

> * The [`toolbar`](../api/treegrid/#toolbar) has options to define both built-in and custom toolbar items.
> * If a toolbar item does not match the built-in items, it will be treated as a custom toolbar item.

## Built-in and custom items in toolbar

TreeGrid have an option to use both built-in and custom toolbar items at same time.

In the below example, `ExpandAll`, `CollapseAll` are built-in toolbar items and `Click` is custom toolbar item.

{% tab template="treegrid/toolbar", sourceFiles="index.ts,index.css,index.html",es5Template="builtincustomitems" %}

```typescript
import { TreeGrid, Edit, Toolbar } from '@syncfusion/ej2-treegrid';
import { EmitType } from '@syncfusion/ej2-base';
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Edit, Toolbar);

let clickHandler: EmitType<ClickEventArgs> = (args: ClickEventArgs) => {
    if (args.item.text === 'Click') {
        alert("Custom toolbar click...");
    }
};

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    toolbar: ['ExpandAll', 'CollapseAll', { text: 'Click', tooltipText: 'Click', prefixIcon: 'e-time', id: 'Click' }],
    toolbarClick: clickHandler,
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true },
    height: 270,
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', isPrimaryKey: true, width: 90, textAlign: 'Right' },
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

<!-- Custom toolbar

Custom toolbar is used to customize the whole toolbar. It can be added by defining `toolbarTemplate` as an HTML element ID.
Actions for this toolbar template items are defined in the [`toolbarClick`](../api/treegrid/#toolbarclick) event.

{% tab template="treegrid/toolbar-template", sourceFiles="index.ts,index.css,index.html", es5Template="customtoolbar" %}

```typescript
import { TreeGrid, Toolbar, Filter } from '@syncfusion/ej2-treegrid';
import { EmitType } from '@syncfusion/ej2-base';
import { sampleData } from './datasource.ts';
import { ClickEventArgs } from '@syncfusion/ej2-navigations';

TreeGrid.Inject(Toolbar, Filter);

let clickHandler: EmitType<ClickEventArgs> = (args: ClickEventArgs) => {
    var target: Element = (<HTMLElement>args.originalEvent.target).closest('.e-toolbar-item');
    if (args.item.id === 'toolbarfilter') {
        treeGridObj.filterByColumn('taskName', 'startswith', 'Testing');
    }
};

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowFiltering: true,
    toolbarTemplate: '#toolbar-template',
    toolbarClick: clickHandler,
    height: 270,
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

```

{% endtab %} -->

## Enable/disable toolbar items

You can enable/disable toolbar items by using the `enableItems` method.

{% tab template="treegrid/toolbar-enable", es5Template="toolbarenable" %}

```typescript
import { TreeGrid, Toolbar, Filter } from '@syncfusion/ej2-treegrid';
import { Button } from '@syncfusion/ej2-buttons';
import { sampleData } from './datasource.ts';
import { ClickEventArgs } from '@syncfusion/ej2-navigations';

TreeGrid.Inject(Toolbar, Filter);
let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowFiltering: true,
    toolbar: ['QuickFilter', 'ClearFilter'],
    toolbarClick: clickHandler,
    height: 200,
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

let enable: Button = new Button({}, '#enable');
let disable: Button = new Button({}, '#disable');

enable.element.onclick = () => {
    treeGridObj.toolbarModule.enableItems([treeGridObj.element.id + '_gridcontrol_QuickFilter', treeGridObj.element.id + '_gridcontrol_ClearFilter'], true);// enable toolbar items.
};

disable.element.onclick = () => {
    treeGridObj.toolbarModule.enableItems([treeGridObj.element.id + '_gridcontrol_QuickFilter', treeGridObj.element.id + '_gridcontrol_ClearFilter'], false);// disable toolbar items.
};

function clickHandler(args: ClickEventArgs): void {
    if (args.item.text === 'QuickFilter') {
        treeGridObj.filterByColumn('taskName', 'startswith', 'Testing');
    }
    if (args.item.text === 'ClearFilter') {
        treeGridObj.clearFiltering();
    }
}

```

{% endtab %}

> You can refer to our [`JavaScript Tree Grid`](https://www.syncfusion.com/javascript-ui-controls/js-tree-grid) feature tour page for its groundbreaking feature representations. You can also explore our JavaScript Tree Grid example [`JavaScript Tree Grid example`](https://ej2.syncfusion.com/demos/#/material/tree-grid/treegrid-overview.html) to knows how to present and manipulate data.