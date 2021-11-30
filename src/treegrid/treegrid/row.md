---
title: "Row"
component: "TreeGrid"
description: "Documentation for row customizations in TreeGrid."
---

# Row

The row represents record details fetched from data source.

## Customize rows

You can customize the appearance of a row by using the [`rowDataBound`](../api/treegrid/#rowdatabound) event.
The [`rowDataBound`](../api/treegrid/#rowdatabound) event triggers for every row. In the event handler, you can get the
`RowDataBoundEventArgs` that contains details of the row.

{% tab template="treegrid/row", sourceFiles="index.ts,index.css,index.html",es5Template="custom" %}

```typescript
import { TreeGrid, RowDataBoundEventArgs } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 275,
    treeColumnIndex: 1,
    rowDataBound: rowBound,
    enableHover: false,
    columns: [
                { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 180 },
                {
                    field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
                },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

function rowBound(args: RowDataBoundEventArgs) {
    if (args.data['duration'] == 0 ) {
        args.row.style.background= '#336c12';
    } else if (args.data['duration'] < 3) {
        args.row.style.background= '#7b2b1d';
    }
}

```

{% endtab %}

## Styling alternate rows

 You can change the treegrid's alternative rows' background color by overriding the `.e-altrow` class.

```css
.e-treegrid .e-altrow {
    background-color: #fafafa;
}
```

Please refer to the following example.

{% tab template="treegrid/alt-row", isDefaultActive=true,es5Template="altrow" %}

```typescript
import { TreeGrid, RowDataBoundEventArgs } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 275,
    treeColumnIndex: 1,
    enableHover: false,
    columns: [
                { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 180 },
                {
                    field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
                },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');


```

{% endtab %}

## Row height

You can customize the row height of treegrid rows through the [`rowHeight`](../api/treegrid/#rowheight) property. The `rowHeight` property
is used to change the row height of entire treegrid rows.

In the below example, the `rowHeight` is set as '60px'.

{% tab template="treegrid/row", sourceFiles="index.ts,index.css,index.html",es5Template="height" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 275,
    rowHeight: 60,
    treeColumnIndex: 1,
    columns: [
                { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 180 },
                {
                    field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
                },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

### Customize row height for particular row

Grid row height for particular row can be customized using the [`rowDataBound`](../api/treegrid/#rowdatabound)
event by setting the `rowHeight` in arguments for each row based on the requirement.

In the below example, the row height for the row with Task ID as '3' is set as '90px' using the `rowDataBound` event.

{% tab template="treegrid/row", sourceFiles="index.ts,index.css,index.html",es5Template="particular" %}

```typescript
import { TreeGrid, RowDataBoundEventArgs } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 275,
    rowDataBound: rowBound,
    treeColumnIndex: 1,
    columns: [
                { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 180 },
                {
                    field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
                },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

function rowBound(args: RowDataBoundEventArgs) {
    if((args.data as TasKDetails).taskID === 3){
        args.rowHeight = 90;
    }
}

interface TasKDetails {
    taskID ?: number;
}

```

{% endtab %}

## Row template

The [`rowTemplate`](../api/treegrid/#rowtemplate) has an option to customise the look and behavior of the treegrid rows. The [`rowTemplate`](../api/treegrid/#rowtemplate) property accepts either the template string or HTML element ID.

{% tab template="treegrid/row-template", sourceFiles="index.ts,index.css,index.html",es5Template="rowtemplate" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { textdata } from './datasource.ts';

    let treegrid: TreeGrid = new TreeGrid(
        {
            dataSource: textdata,
            childMapping: 'Children',
            treeColumnIndex: 0,
            rowTemplate: '#rowtemplate',
            height: 250,
            width: 'auto',
            rowHeight: 83,
            columns: [
                { field: 'EmpID', headerText: 'Employee ID', width: '150' },
                { field: 'Name', headerText: 'Employee Name', width: '150' },
                { field: 'Address', headerText: 'Employee Details', width: '350' }
            ]
        });
    treegrid.appendTo('#TreeGrid');

```

{% endtab %}

The [`rowTemplate`](../api/treegrid/#rowtemplate) property accepts only the TR element.

### Row template with formatting

If the [`rowTemplate`](../api/treegrid/#rowtemplate) is used, the value cannot be  formatted  inside the template using the [`columns.format`](../api/treegrid/column/#format) property. In that case, a function should be defined globally to format the value and invoke it inside the template.

{% tab template="treegrid/row-template-formatting", sourceFiles="index.ts,index.css,index.html",es5Template="row-template-formatting" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { textdata } from './datasource.ts';
import { Internationalization } from '@syncfusion/ej2-base';

let instance: Internationalization = new Internationalization();

(window as DateFormat).format = (value: Date) => {
    return instance.formatDate(value, { skeleton: 'yMd', type: 'date' });
};

interface DateFormat extends Window {
    format?: Function;
}

    let treegrid: TreeGrid = new TreeGrid(
        {
            dataSource: textdata,
            childMapping: 'Children',
            treeColumnIndex: 0,
            rowTemplate: '#rowtemplate',
            height: 250,
            width: 'auto',
            rowHeight: 83,
            columns: [
                { field: 'EmpID', headerText: 'Employee ID', width: '150' },
                { field: 'Address', headerText: 'Employee Details', width: '350' },
                { field: 'DOB', headerText: 'DOB', width: '150' }
            ]
        });
    treegrid.appendTo('#TreeGrid');

```

{% endtab %}

### Limitations

Row template feature is not compatible with all the features which are available in treegrid and it has limited features support. Here we have listed out the features which are compatible with row template feature.

* Filtering
* Paging
* Sorting
* Scrolling
* Searching
* Rtl
* Context Menu
* State Persistence

## Detail template

The detail template provides additional information about a particular row. By expanding the parent row the child rows are expanded along with their detail template. The [`detailTemplate`](../api/treegrid/#detailtemplate) property accepts either the template string or HTML element ID.

To use detail template, inject the DetailRow module in the TreeGrid.

{% tab template="treegrid/detail-template", sourceFiles="index.ts,index.html",es5Template="detailtemplate" %}

```typeScript
import { TreeGrid, DetailRow } from '@syncfusion/ej2-treegrid';
import { textdata } from './datasource.ts';
import { Internationalization } from '@syncfusion/ej2-base';

TreeGrid.Inject(DetailRow);

let instance: Internationalization = new Internationalization();

(window as DateFormat).format = (value: Date) => {
    return instance.formatDate(value, { skeleton: 'yMd', type: 'date' });
};

interface DateFormat extends Window {
    format?: Function;
}

    let treegrid: TreeGrid = new TreeGrid(
        {
            dataSource: textdata,
            childMapping: 'Children',
            treeColumnIndex: 0,
            detailTemplate: '#detailtemplate',
            width: 'auto',
            columns: [
                { field: 'Name', headerText: 'First Name', width: '170' },
                { field: 'Designation', headerText: 'Designation', width: '180' },
                { field: 'EmpID', headerText: 'EmployeeID', width: '110'},
                { field: 'Country', headerText: 'Country' , width: '90'},
            ]
        });
    treegrid.appendTo('#TreeGrid');

```

{% endtab %}

## Drag and drop

The TreeGrid rows can be reordered, dropped to another TreeGrid or custom control by enabling the [`allowRowDragAndDrop`](../api/treegrid/#allowrowdraganddrop) to true.

To use row drag and drop, inject the `RowDD` module in the TreeGrid.

### Drag and drop within TreeGrid

The TreeGrid row drag and drop allows you to drag and drop TreeGrid rows on the same TreeGrid using drag icon. To enable row drag and drop, set the [`allowRowDragAndDrop`](../api/treegrid/#allowrowdraganddrop) to true. It provides the way to drop the row above, below or child to the target row with respective to the target row position.

{% tab template="treegrid/draganddrop-single",es5Template="dragdrop" %}

```typescript
import { TreeGrid, RowDD } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(RowDD);

let treegrid: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    treeColumnIndex: 1,
    childMapping: 'subtasks',
    allowRowDragAndDrop: true,
    heigth:300,
    selectionSettings: { type: 'Multiple' },
    columns: [
            { field: 'taskID', headerText: 'Task ID', isPrimaryKey: true, width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180 },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});
treegrid.appendTo('#TreeGrid');

```

{% endtab %}

> * Selection feature must be enabled for row drag and drop.
> * For multiple row selection, the [`type`](../api/treegrid/selectionSettings/#type) property must be set to `multiple`.

### Drag and drop to another TreeGrid

To drag and drop between two TreeGrid, enable the [`allowRowDragAndDrop`](../api/treegrid/#allowrowdraganddrop) property and specify the target TreeGrid ID in [`targetID`](../api/treegrid/rowDropSettings/#targetid) property of rowDropSettings.

{% tab template="treegrid/draganddrop",es5Template="dragdrop" %}

```typescript
import { TreeGrid, RowDD } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(RowDD);

let treegrid: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    treeColumnIndex: 1,
    childMapping: 'subtasks',
    allowRowDragAndDrop: true,
    rowDropSettings: { targetID: 'destTree' },
    selectionSettings: { type: 'Multiple' },
    columns: [
            { field: 'taskID', headerText: 'Task ID', isPrimaryKey: true, width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180 },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});
treegrid.appendTo('#TreeGrid');

let destTree: TreeGrid = new TreeGrid({
    dataSource: [],
    treeColumnIndex: 1,
    childMapping: 'subtasks',
    allowRowDragAndDrop: true,
    rowDropSettings: { targetID: 'TreeGrid' },
    selectionSettings: { type: 'Multiple' },
    columns: [
            { field: 'taskID', headerText: 'Task ID', isPrimaryKey: true, width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180 },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});
destTree.appendTo('#destTree');

```

{% endtab %}

### Drag and drop events

The following events are triggered while drag and drop the treegrid rows.

[`rowDragStartHelper`](../api/treegrid/#rowdragstarthelper) - Triggers when click the drag icon or treegrid row and this event is used to customize the drag element based on user criteria.<br/>
[`rowDragStart`](../api/treegrid/#rowdragstart) -Triggers when starts to drag the treegrid row. <br/>
[`rowDrag`](../api/treegrid/#rowdrag) - Triggers while dragging the treegrid row. <br/>
[`rowDrop`](../api/treegrid/#rowdrop) - Triggers when a drag element is dropped on the target element. <br/>

> You can refer to our [`JavaScript Tree Grid`](https://www.syncfusion.com/javascript-ui-controls/js-tree-grid) feature tour page for its groundbreaking feature representations. You can also explore our JavaScript Tree Grid example [`JavaScript Tree Grid example`](https://ej2.syncfusion.com/demos/#/material/tree-grid/treegrid-overview.html) to knows how to present and manipulate data.