---
title: "Cell"
component: "TreeGrid"
description: "Learn how to customize the Essential JS 2 TreeGrid cells with styling, text wrapping, and tooltips."
---

# Cell

## Displaying the HTML content

The HTML tags can be displayed in the TreeGrid header and content by enabling the [`disableHtmlEncode`](../api/treegrid/column/#disablehtmlencode) property.

{% tab template="treegrid/cell", sourceFiles="index.ts,index.html,datasource.ts",es5Template="htmlcontent" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { htmlData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: htmlData,
    childMapping: 'subtasks',
    height: 300,
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: '<span> Task ID </span>', disableHtmlEncode: true, width: 140, textAlign: 'Right' },
        { field: 'taskName', headerText: '<span> Task Name </span>', disableHtmlEncode: false, width: 180 },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
        { field: 'progress', headerText: 'Progress', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Customize cell styles

The appearance of cells can be customized by using the [`queryCellInfo`](../api/treegrid/#querycellinfo) event.
The [`queryCellInfo`](../api/treegrid/#querycellinfo) event triggers for every cell. In that event handler, you can get
`QueryCellInfoEventArgs` that contains the details of the cell.

{% tab template="treegrid/cell", sourceFiles="index.ts,index.html,index.css",es5Template="customcell" %}

```typescript
import { TreeGrid, QueryCellInfoEventArgs } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 300,
    queryCellInfo: customiseCell,
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
        { field: 'taskName', headerText: 'Task Name', width: 180 },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
        { field: 'progress', headerText: 'Progress', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

function customiseCell(args: QueryCellInfoEventArgs) {
    if (args.column.field === 'progress' && +args.cell.innerHTML > 90 && +args.cell.innerHTML <= 100){
        args.cell.setAttribute('style', 'background-color:#336c12;color:white;');
    } else if (+args.cell.innerHTML > 20 && args.column.field === 'progress') {
        args.cell.setAttribute('style', 'background-color:#7b2b1d;color:white;');
    }
}

```

{% endtab %}

## Auto wrap

The auto wrap allows the cell content of the treegrid to wrap to the next line when it exceeds the boundary of the cell width. The Cell Content wrapping works based on the position of white space between words.
To enable auto wrap, set the [`allowTextWrap`](../api/treegrid/#allowtextwrap) property to `true`.
You can configure the auto wrap mode by setting the [`textWrapSettings.wrapMode`](../api/treegrid/#textwrapsettings) property.

There are three types of `wrapMode`. They are:

* **`Both`**: `Both` value is set by default. Auto wrap will be enabled for both the content and the header.
* **`Header`**: Auto wrap will be enabled only for the header.
* **`Content`**: Auto wrap will be enabled only for the content.

Note: When a column width is not specified, then auto wrap of columns will be adjusted with respect to the treegrid's width.

In the following example, the `textWrapSettings.wrapMode` is set to `Content`.

{% tab template="treegrid/cell", es5Template="autowrap" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 300,
    allowTextWrap: true,
    textWrapSettings: { wrapMode: 'Content' },
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
        { field: 'taskName', headerText: 'Task Name', width: 75 },
        {
            field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
        },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Custom Attributes

You can customize the treegrid cells by adding a CSS class to the [`customAttribute`](../api/treegrid/column/#customattributes) property of the column.

```CSS
.e-attr {
    background: '#d7f0f4';
}
```

```typescript
{
    field: 'taskID', headerText: 'Task ID', width: 90, customAttributes: {class: "e-attr"}, textAlign: 'Right'
}
```

In the below example, we have customized the cells of `TaskID` and `StartDate` columns.

{% tab template="treegrid/cell-attributes", es5Template="cellstyle" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 300,
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', width: 90, customAttributes: {class: "e-attr"}, textAlign: 'Right' },
        { field: 'taskName', headerText: 'Task Name', width: 160 },
        {
            field: 'startDate', headerText: 'Start Date', width: 90, customAttributes: {class: "e-attr"}, textAlign: 'Right', type: 'date',format: 'yMd'
        },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Grid Lines

The [`gridLines`](../api/treegrid/#gridlines) have option to display cell border and it can be defined by the
[`gridLines`](../api/treegrid/#gridlines) property.

The available modes of grid lines are:

| Modes | Actions |
|-------|---------|
| Both | Displays both the horizontal and vertical grid lines.|
| None | No grid lines are displayed.|
| Horizontal | Displays the horizontal grid lines only.|
| Vertical | Displays the vertical grid lines only.|
| Default | Displays grid lines based on the theme.|

{% tab template="treegrid/cell", es5Template="gridlines" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 300,
    gridLines: 'Both',
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
        { field: 'taskName', headerText: 'Task Name', width: 160 },
        {
            field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
        },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

>By default, the treegrid renders with `Default` mode.

## Clip Mode

The clip mode provides options to display its overflow cell content and it can be defined by the [`columns.clipMode`](../api/treegrid/column/#clipmode) property.

There are three types of [`clipMode`](../api/treegrid/column/#clipmode). They are:

* **`Clip`**: Truncates the cell content when it overflows its area.
* **`Ellipsis`**: Displays ellipsis when the cell content overflows its area.
* **`EllipsisWithTooltip`**: Displays ellipsis when the cell content overflows its area, also it will display the tooltip while hover on ellipsis is applied.

{% tab template="treegrid/cell", es5Template="clipmode" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { complexData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: complexData,
    childMapping: 'subtasks',
    height: 300,
    gridLines: 'Both',
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
        { field: 'taskName', headerText: 'Task Name', clipMode: 'Clip', width: 70 },
        { field: 'assignee.firstName', headerText: 'Assignee', clipMode: 'Ellipsis', width: 30},
        { field: 'priority', headerText: 'Priority', clipMode: 'EllipsisWithTooltip', width: 30 },
        { field: 'duration', headerText: 'Duration', width: 30, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

>By default, [`columns.clipMode`](../api/treegrid/column/#clipmode) value is `Ellipsis`.