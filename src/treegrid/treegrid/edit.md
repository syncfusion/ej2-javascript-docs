---
title: "Editing"
component: "TreeGrid"
description: "Learn how to perform CRUD operations in various edit modes, and use different cell editors in the Essential JS 2 TreeGrid control."
---

# Editing

The TreeGrid component has options to dynamically insert, delete and update records.
Editing feature is enabled by using [`editSettings`](../api/treegrid/#editsettings) property and it requires a primary key column for CRUD operations.
To define the primary key, set [`columns.isPrimaryKey`](../api/treegrid/column/#isprimarykey) to `true` in particular column.

To use CRUD, inject the [`Edit`](../api/treegrid/#editmodule) module in treegrid.

{% tab template="treegrid/edit",es5Template="editing" %}

```typescript
import { TreeGrid, Edit } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Edit);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Cell' },
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', isPrimaryKey: true, width: 90, textAlign: 'Right'},
        { field: 'taskName', headerText: 'Task Name', width: 180 },
        { field: 'priority', headerText: 'Priority', width: 90 },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ],
    height: 270
});
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

> * You can disable editing for a particular column, by specifying [`columns.allowEditing`](../api/treegrid/column/#allowediting) to `false`.

## Toolbar with edit option

The treegrid toolbar has the built-in items to execute Editing actions.
You can define this by using the [`toolbar`](../api/treegrid/#toolbar) property.

{% tab template="treegrid/edit",es5Template="toolbaredit" %}

```typescript
import { TreeGrid, Edit, Toolbar } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Edit, Toolbar);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Row' },
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', isPrimaryKey: true, width: 90, textAlign: 'Right'},
        { field: 'taskName', headerText: 'Task Name', width: 180 },
        { field: 'priority', headerText: 'Priority', width: 90 },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ],
    height: 270
});
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Cell edit type and its params

The [`columns.editType`](../api/treegrid/column/#edittype) is used to customize the edit type of the particular column.
You can set the [`columns.editType`](../api/treegrid/column/#edittype) based on data type of the column.

* `numericedit` - [`NumericTextBox`](../numerictextbox) component for integers, double, and decimal data types.

* `defaultedit` - [`TextBox`](../textbox) component for string data type.

* `dropdownedit` - [`DropDownList`](../drop-down-list) component for list data type.

* `booleanedit` - [`CheckBox`](../check-box) component for boolean data type.

* `datepickeredit` - [`DatePicker`](../datepicker) component for date data type.

* `datetimepickeredit` - [`DateTimePicker`](../datetimepicker) component for date time data type.

Also, you can customize model of the [`columns.editType`](../api/treegrid/column/#edittype) component through the [`columns.edit.params`](../api/treegrid/column/#edit).

The following table describes cell edit type component and their corresponding edit params of the column.

Component |Example
-----|-----
[`NumericTextBox`](../numerictextbox) | params: { decimals: 2, value: 5 }
[`TextBox`](../textbox) | -
[`DropDownList`](../drop-down-list) | params: { value: 'Germany' }
[`Checkbox`](../check-box) | params: { checked: true}
[`DatePicker`](../datepicker) | params: { format:'dd.MM.yyyy' }
[`DateTimePicker`](../datetimepicker) | params: { value: new Date() }

{% tab template="treegrid/edit",es5Template="celledit" %}

```typescript
import { TreeGrid, Edit, Toolbar } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Edit, Toolbar);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    toolbar: ['Add', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Row' },
    treeColumnIndex: 1,
    columns: [
        {
            field: 'taskID', headerText: 'Task ID', isPrimaryKey: true, textAlign: 'Right', width: 100
        },
        {
            field: 'taskName', headerText: 'Task Name', editType: 'stringedit', width: 170
        },
        {
            field: 'startDate', headerText: 'Start Date', textAlign: 'Right', width: 180,
            editType: 'datetimepickeredit', edit: { params: { format: 'M/d/y hh:mm a' } },
            format: { format: 'M/d/y hh:mm a', type: 'dateTime' }
        },
        {
            field: 'approved', headerText: 'Approved', width: 110, editType: 'booleanedit',
            type: 'boolean', displayAsCheckBox: true
        },
        {
            field: 'progress', headerText: 'Progress', textAlign: 'Right', width: 120,
            editType: 'numericedit', edit: { params: { format: 'n' } }
        },
        { field: 'priority', headerText: 'Priority', width: 110, editType: 'dropdownedit' }
    ]
    height: 270
});
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

> If edit type is not defined in the column, then it will be considered as the `stringedit` type (Textbox component).

## Cell Edit Template

The cell edit template is used to add a custom component for a particular column by invoking the following functions:

* `create` - It is used to create the element at the time of initialization.

* `write` - It is used to create the custom component or assign default value at the time of editing.

* `read` - It is used to read the value from the component at the time of save.

* `destroy` - It is used to destroy the component.

{% tab template="treegrid/edit",es5Template="customcelledit" %}

```typescript
import { TreeGrid, Edit, Toolbar, Column } from '@syncfusion/ej2-treegrid';
import { AutoComplete } from '@syncfusion/ej2-dropdowns';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Edit, Toolbar);

let elem: HTMLElement;
let autoCompleteObj: AutoComplete;
let treeGridObj: TreeGrid = new TreeGrid(
    {
        dataSource: sampleData,
        childMapping: 'subtasks',
        treeColumnIndex: 1,
        height: 400,
        editSettings: {
            allowAdding: true,
            allowEditing: true,
            allowDeleting: true,
            mode: 'Cell',
            newRowPosition: 'Below'

        },
        toolbar: ['Add', 'Delete', 'Update', 'Cancel'],
        columns: [
            {
                field: 'taskID', headerText: 'Task ID', isPrimaryKey: true, textAlign: 'Right', width: 90
            },
            { field: 'taskName', headerText: 'Task Name', editType: 'stringedit', edit: {
                create: () => {
                    elem = document.createElement('input');
                    return elem;
                },
                read: () => {
                    return autoCompleteObj.value;
                },
                destroy: () => {
                    autoCompleteObj.destroy();
                },
                write: (args: { rowData: Object, column: Column }) => {
                    autoCompleteObj = new AutoComplete({
                        dataSource: <{key: string, value: any}[]>treeGridObj.grid.dataSource,
                        fields: { value: 'taskName' },
                        value: args.rowData[args.column.field]
                    });
                    autoCompleteObj.appendTo(elem);
                }
            },
            width: 180  },
            { field: 'startDate', headerText: 'Start Date', textAlign: 'Right', width: 130, editType: 'datepickeredit', type: 'date', format: 'yMd' },
            {
                field: 'duration', headerText: 'Duration', textAlign: 'Right', width: 80, editType: 'numericedit', edit: { params: {  format: 'n'}}
            }
        ]
    });
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Edit Modes

TreeGrid supports the following types of edit modes, they are:

* Cell
* Row
* Dialog
* Batch

### Cell

In Cell edit mode, when you double click on a cell, it is changed to edit state.
You can change the cell value and save to the data source.
To enable Cell edit, set the [`editSettings.mode`](../api/treegrid/editSettingsModel/#mode) as `Cell`.

{% tab template="treegrid/edit",es5Template="cell" %}

```typescript
import { TreeGrid, Edit, Toolbar } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Edit, Toolbar);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    toolbar: ['Add', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Cell' },
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', isPrimaryKey: true, width: 90, textAlign: 'Right'},
        { field: 'taskName', headerText: 'Task Name', width: 180 },
        {
            field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', editType: 'datepickeredit', type: 'date', format: 'yMd'
        },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ],
    height: 270
});
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

> Cell edit mode is default mode of editing.

### Row

In Row edit mode, when you start editing the currently selected record, the entire row is changed to edit state.
You can change the cell values of the row and save edited data to the data source.
To enable Row edit, set the [`editSettings.mode`](../api/treegrid/editSettingsModel/#mode) as `Row`.

{% tab template="treegrid/edit",es5Template="row" %}

```typescript
import { TreeGrid, Edit, Toolbar } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Edit, Toolbar);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Row' },
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', isPrimaryKey: true, width: 90, textAlign: 'Right'},
        { field: 'taskName', headerText: 'Task Name', width: 180 },
        {
            field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', editType: 'datepickeredit', type: 'date', format: 'yMd'
        },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ],
    height: 270
});
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

### Dialog

In Dialog edit mode, when you start editing the currently selected row, data will be shown on a dialog.
You can change the cell values and save edited data to the data source.
To enable Dialog edit, set the [`editSettings.mode`](../api/treegrid/editSettingsModel/#mode) as `Dialog`.

{% tab template="treegrid/edit",es5Template="dialog" %}

```typescript
import { TreeGrid, Edit, Toolbar } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Edit, Toolbar);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Dialog' },
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', isPrimaryKey: true, width: 90, textAlign: 'Right'},
        { field: 'taskName', headerText: 'Task Name', width: 180 },
        {
            field: 'startDate', headerText: 'Start Date', width: 90, editType: 'datepickeredit', textAlign: 'Right', type: 'date',format: 'yMd'
        },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ],
    height: 270
});
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

### Batch

In Batch edit mode, when you double-click on the Tree Grid cell, then the target cell changed to edit state. You can bulk save (added, changed and deleted data in the single request) to data source by click on the toolbar's `Update` button or by externally invoking the [`batchSave`](../api/treegrid/edit/#batchsave) method. To enable Batch edit, set the [`editSettings.mode`](../api/grid/editSettings/#mode) as `Batch`.

{% tab template="treegrid/edit",es5Template="batch" %}

```typescript
import { TreeGrid, Edit, Toolbar } from '@syncfusion/ej2-treegrid';
import { projectData } from './datasource.ts';

TreeGrid.Inject(Edit, Toolbar);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: projectData,
    idMapping: 'TaskID',
    parentIdMapping: 'parentID',
    toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Batch', newRowPosition: 'Below' },
    treeColumnIndex: 1,
    columns: [
        { field: 'TaskID', headerText: 'Task ID', isPrimaryKey: true, width: 90, textAlign: 'Right'},
        { field: 'TaskName', headerText: 'Task Name', width: 180 },
        {
            field: 'StartDate', headerText: 'Start Date', width: 90, editType: 'datepickeredit', textAlign: 'Right', type: 'date',format: 'yMd'
        },
        { field: 'Duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ],
    height: 270
});
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Dialog template

The dialog template editing provides an option to customize the default behavior of dialog editing. Using the dialog template, you can render your own editors by defining the [`editSettings.mode`](../api/treegrid/editSettingsModel/#mode) as `Dialog` and [`template`](../api/treegrid/editSettingsModel/#template) as SCRIPT element ID or HTML string which holds the template.

In some cases, you need to add the new field editors in the dialog which are not present in the column model. In that situation, the dialog template will help you to customize the default edit dialog.

In the following sample, treegrid enabled with dialog template editing.

{% tab template="treegrid/dialog-template", sourceFiles="index.ts,index.css,index.html",es5Template="dialogtemplate" %}

```typescript
import { TreeGrid, Edit, Toolbar, DialogEditEventArgs, SaveEventArgs } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';
import { DataUtil } from '@syncfusion/ej2-data';
import { DatePicker } from '@syncfusion/ej2-calendars';
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { CheckBox } from '@syncfusion/ej2-buttons';
import { NumericTextBox } from '@syncfusion/ej2-inputs';

TreeGrid.Inject(Edit, Toolbar);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Dialog',
    template: '#dialogtemplate' },
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', isPrimaryKey: true, width: 90, textAlign: 'Right'},
        { field: 'taskName', headerText: 'Task Name', width: 180 },
        {
            field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
        },
        { field: 'progress', headerText: 'Progress', width: 80, textAlign: 'Right' }
    ],
    height: 270,
    actionBegin: (args: SaveEventArgs) => {
        if (args.requestType === 'save') {
            // cast string to integer value.
            args.data['progress'] = parseFloat(args.form.querySelector("#progress").value);
        }
    },
    actionComplete: (args: DialogEditEventArgs) => {
        if ((args.requestType === 'beginEdit' || args.requestType === 'add')) {
            // Add Validation Rules
            args.form.ej2_instances[0].addRules('progress', {max: 100});
            // EJ2-control Rendering
            let priorityData: {}[] = DataUtil.distinct(treeGridObj.grid.dataSource, 'priority',true);
            new DropDownList({value: args.rowData.priority, popupHeight: '200px', floatLabelType: 'Always',
                dataSource: priorityData, fields: {text: 'priority', value: 'priority'}, placeholder: 'Priority'}, args.form.elements.namedItem('priority') as HTMLInputElement);

            new DatePicker({value: args.rowData.startDate, floatLabelType: 'Always', placeholder: 'Start Date'}, args.form.elements.namedItem('startDate') as HTMLInputElement)

            new DatePicker({value: args.rowData.endDate, floatLabelType: 'Always', placeholder: 'End Date'}, args.form.elements.namedItem('endDate') as HTMLInputElement)

            new CheckBox({ label: 'Approved', checked: args.rowData.approved }, args.form.elements.namedItem('approved'));

            new NumericTextBox({value: args.rowData.progress, format: 'n', placeholder: 'Progress', floatLabelType: 'Always' }, args.form.elements.namedItem('progress') as HTMLInputElement );
             // Set initail Focus
            if (args.requestType === 'beginEdit') {
                (args.form.elements.namedItem('taskName')as HTMLInputElement).focus();
            }
        }
    }
});
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

> The template form editors should have **name** attribute.

### Template context

The Essential JS2 packages has a built-in template engine. Using the template engine, you can access the row information inside the HTML element and bind the attributes, values, or elements based on this row information.

The following properties will be available at the time of template execution.

| Property Name | Usage |
|---------------|--------|
| <kbd>isAdd</kbd> | A Boolean property; it defines whether the current row should be a new record or not.

In the following code example, the `OrderID` textbox has been disabled by using the `isAdd` property.

```html
// The disabled attributes will be added based on the isAdd property.
<input id="taskID" name="taskID" type="text" value=${if(isAdd)} '' ${else} ${taskID} ${/if}  ${if(isAdd)}'' ${else} disabled ${/if}/>

```

The following code example illustrates rendering the `taskID` textbox, when a new record is added.

```html

${if(isAdd)}
<div class="form-group col-md-6">
    <div class="e-float-input e-control-wrapper">
        <input id="taskID" name="taskID" type="text" value=${if(isAdd)} '' ${else} ${taskID} ${/if}  ${if(isAdd)}'' ${else} disabled ${/if}/>
        <span class="e-float-line"></span>
        <label class="e-float-text e-label-top" for="OrderID">Task ID</label>
    </div>
</div>
${/if}

```

> The dialog template syntax supports the ES6 expression string literals, and you can refer to the [`Template Engine`](../common/template-engine/) for more template syntax.

### Render editors as components

You can convert the form editors to EJ2 controls in the [`actionComplete`](../api/treegrid/#actioncomplete) event based on the `requestType` as `beginEdit` or `add`.

The following code example illustrates rendering the drop-down list control in the `actionComplete` event.

```typescript

    actionComplete: (args: DialogEditEventArgs) => {
        if ((args.requestType === 'beginEdit' || args.requestType === 'add')) {
            let priorityData: {}[] = DataUtil.distinct(treeGridObj.grid.dataSource, 'priority',true);
            new DropDownList({value: args.rowData.priority, popupHeight: '200px', floatLabelType: 'Always',
                dataSource: priorityData, fields: {text: 'priority', value: 'priority'}, placeholder: 'Priority'}, args.form.elements.namedItem('priority') as HTMLInputElement);
        }
    }

```

### Get value from editor

You can read, format, and update the current editor value in the [`actionBegin`](../api/treegrid/#actionbegin) event at the time of setting `requestType` to `save`.

In the following code example, the `progress` value has been formatted and updated.

``` typescript
    actionBegin: (args: SaveEventArgs) => {
        if (args.requestType === 'save') {
            // cast string to integer value.
            args.data['progress'] = parseFloat(args.form.querySelector("#progress").value);
        }
    }

```

### Set focus to editor

By default, the first input element in the dialog will be focused while opening the dialog.
If the first input element is in disabled or hidden state, focus the valid input element in the
[`actionComplete`](../api/treegrid/#actioncomplete)
event based on `requestType` as `beginEdit`.

```typescript

    actionComplete: (args: DialogEditEventArgs) => {
        // Set initail Focus
        if (args.requestType === 'beginEdit') {
            (args.form.elements.namedItem('taskName')as HTMLInputElement).focus();
        }
    }

```

### Adding validation rules for custom editors

If you have used additional fields that are not present in the column model, then add the validation rules to the [`actionComplete`](../api/treegrid/#actioncomplete) event.

```typescript

    actionComplete: (args: DialogEditEventArgs) => {
        if ((args.requestType === 'beginEdit' || args.requestType === 'add')) {
            // Add Validation Rules
            args.form.ej2_instances[0].addRules('progress', {max: 100});
        }
    }

```

## Adding row position

The TreeGrid control provides the support to add the new row in the top, bottom, above selected row, below selected row and child position of tree grid content using [`editSettings.newRowPosition`](../api/treegrid/editSettingsModel/#newrowposition) property. By default, a new row will be added at the top of the treegrid.

The following examples shows how to set new row position as `Child` in tree grid.

{% tab template="treegrid/edit",es5Template="newrow" %}

```typescript
import { TreeGrid, Edit, Toolbar } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Edit, Toolbar);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    toolbar: ['Add', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, newRowPosition: 'Child', mode: 'Cell' },
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', isPrimaryKey: true, width: 90, textAlign: 'Right'},
        { field: 'taskName', headerText: 'Task Name', width: 180 },
        {
            field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', editType: 'datepickeredit', type: 'date', format: 'yMd'
        },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ],
    height: 270
});
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Command column

The command column provides an option to add CRUD action buttons in a column. This can be defined by the [`column.commands`](../api/treegrid/column/#commands) property.

The available built-in command buttons are:

| Command Button | Actions |
|----------------|---------|
| Edit | Edit the current row.|
| Delete | Delete the current row.|
| Save | Update the edited row.|
| Cancel | Cancel the edited state. |

{% tab template="treegrid/edit", sourceFiles="index.ts,index.html",es5Template="commandcolumn" %}

```typescript
import { TreeGrid, CommandColumn, Edit } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(CommandColumn, Edit);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Row' },
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', isPrimaryKey: true, width: 90, textAlign: 'Right'},
        { field: 'taskName', headerText: 'Task Name', width: 180 },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
        {
            headerText: 'Manage Records', width: 130,
            commands: [{ type: 'Edit', buttonOption: { iconCss: ' e-icons e-edit', cssClass: 'e-flat' } },
                { type: 'Delete', buttonOption: { iconCss: 'e-icons e-delete', cssClass: 'e-flat' } },
                { type: 'Save', buttonOption: { iconCss: 'e-icons e-update', cssClass: 'e-flat' } },
                { type: 'Cancel', buttonOption: { iconCss: 'e-icons e-cancel-icon', cssClass: 'e-flat' } }]
        }
    ],
    height: 270
});
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

### Custom command

 The custom command buttons can be added in a column by using the [`column.commands`](../api/treegrid/column/#commands) property and
the action for the custom buttons can be defined in the [`buttonOption.click`](../api/grid/commandButtonOptions/#click) event.

{% tab template="treegrid/edit", sourceFiles="index.ts,index.html", es5Template="customcommand" %}

```typescript
import { TreeGrid, CommandColumn, Edit, IRow, Column } from '@syncfusion/ej2-treegrid';
import { closest } from '@syncfusion/ej2-base';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(CommandColumn, Edit);

let onClick = (args: Event) => {
    let rowIndex: number = (<HTMLTableRowElement>closest(args.target as Element, '.e-row')).rowIndex;
    let data: Object = treeGridObj.getCurrentViewRecords();
    alert(JSON.stringify(data[rowIndex]));
}

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Row' },
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', isPrimaryKey: true, width: 90, textAlign: 'Right'},
        { field: 'taskName', headerText: 'Task Name', width: 180 },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
        { headerText: 'Commands', width: 120, commands: [{ buttonOption: { content: 'Details', cssClass: 'e-flat', click: onClick } }]},
    ],
    height: 270
});
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Confirmation messages

### Delete confirmation

The delete confirm dialog can be shown when deleting a record by defining the [`showDeleteConfirmDialog`](../api/treegrid/editSettingsModel/#showdeleteconfirmdialog) as `true`

{% tab template="treegrid/edit",es5Template="deleteconfirm" %}

```typescript
import { TreeGrid, Edit, Toolbar } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Edit, Toolbar);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    toolbar: ['Add', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, showDeleteConfirmDialog: true, mode: 'Cell' },
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', isPrimaryKey: true, width: 90, textAlign: 'Right'},
        { field: 'taskName', headerText: 'Task Name', width: 180 },
        {
            field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', editType: 'datepickeredit', type: 'date', format: 'yMd'
        },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ],
    height: 270
});
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

> The `showDeleteConfirmDialog` supports all type of edit modes.

## Column validation

Column validation allows you to validate the edited or added row data and it display errors for invalid fields before saving data.
TreeGrid uses `Form Validator` component for column validation.
You can set validation rules by defining the [`columns.validationRules`](../api/treegrid/column/#validationrules).

{% tab template="treegrid/edit",es5Template="editvalidation" %}

```typescript
import { TreeGrid, Edit, Toolbar } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Edit, Toolbar);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    toolbar: ['Add', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, showDeleteConfirmDialog: true, mode: 'Cell' },
    treeColumnIndex: 1,
    columns: [
        {
            field: 'taskID', headerText: 'Task ID', isPrimaryKey: true, textAlign: 'Right',
            validationRules: { required: true, number: true }, width: 100
        },
        {
            field: 'taskName', headerText: 'Task Name', editType: 'stringedit',
            validationRules: { required: true }, width: 170
        },
        {
            field: 'startDate', headerText: 'Start Date', textAlign: 'Right', width: 180,
            editType: 'datetimepickeredit', edit: { params: { format: 'M/d/y hh:mm a' } },
            format: { format: 'M/d/y hh:mm a', type: 'dateTime' }, validationRules: { date: true }
        },
        {
            field: 'approved', headerText: 'Approved', width: 110, editType: 'booleanedit',
            type: 'boolean', displayAsCheckBox: true
        },
        {
            field: 'progress', headerText: 'Progress', textAlign: 'Right', width: 120,
            editType: 'numericedit', validationRules: { number: true, min: 0 }, edit: { params: { format: 'n' } }
        },
        { field: 'priority', headerText: 'Priority', width: 110, editType: 'dropdownedit', validationRules: { required: true } }
    ],
    height: 270
});
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Custom validation

You can define your own custom validation rules for the specific columns by using `Form Validator custom rules`.

In the below demo, custom validation applied for `Priority` column.

{% tab template="treegrid/edit",es5Template="customedit" %}

```typescript
import { TreeGrid, Edit, Toolbar } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Edit, Toolbar);

let customFn: (args: { [key: string]: string }) => boolean = (args: { [key: string]: string }) => {
    return args['value'].length <= 8;
};

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    toolbar: ['Add', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, showDeleteConfirmDialog: true, mode: 'Cell' },
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', isPrimaryKey: true, width: 90, textAlign: 'Right'},
        { field: 'taskName', headerText: 'Task Name', width: 180 },
        {
            field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', editType: 'datepickeredit', type: 'date', format: 'yMd'
        },
        { field: 'priority', headerText: 'Priority', width: 80, validationRules: { required: true, minLength: [customFn, 'Value should be within 8 letters'] } }
    ],
    height: 270
});
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Persisting data in server

Edited data can be persisted in the database using the RESTful web services.

All the CRUD operations in the treegrid are done through [`DataManager`](../data). The `DataManager` has an option to bind all the CRUD related data in server-side.

> For your information, the ODataAdaptor persists data in the server as per OData protocol.

In the following section, we have explained how to perform CRUD operation in server-side using the [`UrlAdaptor`](../../data/adaptors.html#url-adaptor) and `RemoteSave Adaptor`.

### URL adaptor

You can use the [`UrlAdaptor`](../../data/adaptors.html#url-adaptor) of `DataManager` when binding data source from remote data.
In the initial load of treegrid, data are fetched from remote data and bound to the treegrid using `url` property of `DataManager`.
You can map The CRUD operation in treegrid can be mapped to server-side Controller actions using the properties `insertUrl`, `removeUrl`, `updateUrl` and `batchUrl`.

The following code example describes the above behavior.

```typescript

import { TreeGrid, Edit, Toolbar } from '@syncfusion/ej2-treegrid';
import { DataManager, UrlAdaptor } from '@syncfusion/ej2-data';

TreeGrid.Inject(Edit, Toolbar);

let data: DataManager = new DataManager({
    url: "Home/DataSource",
    updateUrl: "Home/Update",
    insertUrl: "Home/Insert",
    removeUrl: "Home/Delete",
    batchUrl: "Home/Remove",
    adaptor: new UrlAdaptor
});

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: data,
    idMapping: 'TaskID',
    parentIdMapping: 'parentItem',
    hasChildMapping: 'isParent',
    toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Row', newRowPosition: 'Below' },
    treeColumnIndex: 1,
    columns: [
        { field: 'TaskID', headerText: 'Task ID', isPrimaryKey: true, width: 90, textAlign: 'Right'},
        { field: 'TaskName', headerText: 'Task Name', width: 180 },
        {
            field: 'StartDate', headerText: 'Start Date', width: 90, textAlign: 'Right', editType: 'datepickeredit', type: 'date', format: 'yMd'
        },
        { field: 'Priority', headerText: 'Priority', width: 80, validationRules: { required: true } }
    ],
    height: 270
});
treeGridObj.appendTo('#TreeGrid');

```

Also, when using the `UrlAdaptor`, you need to return the data as JSON from the controller action and the JSON object must contain a property as `result` with dataSource as its value and one more property `count` with the dataSource total records count as its value.

The following code example describes the above behavior.

```typescript

public ActionResult DataSource(DataManager dm)
{
    var DataSource = TreeData.GetTree();
    DataOperations operation = new DataOperations();
    if (dm.Where != null && dm.Where.Count > 0)
    {
        DataSource = operation.PerformFiltering(DataSource, dm.Where, "and");   //perform filtering  and maintain child records on Expand/Collapse operation
    }
    var count = DataSource.ToList<TreeData>().Count();
    if (dm.Skip != 0)
    {
        DataSource = operation.PerformSkip(DataSource, dm.Skip);   //Paging
    }
    if (dm.Take != 0)
    {
        DataSource = operation.PerformTake(DataSource, dm.Take);
    }
    return dm.RequiresCounts ? Json(new { result = DataSource, count = count }) : Json(DataSource);
}

```

### Insert record

Using the `insertUrl` property, you can specify the controller action mapping URL to perform insert operation on the server-side.

The following code example describes the above behavior and also we have inserted new record based on the newRowPosition TreeGrid editSettings as "Below".

```typescript

public void Insert(TreeGridData value, int relationalKey)
{
    var i = 0;
    for (; i < TreeData.tree.Count; i++)
    {
        if (TreeData.tree[i].TaskID == relationalKey)
        {
            break;
        }
    }
    i += FindChildRecords(relationalKey); // Inserted new record when newRowPosition API is in "Below".
    TreeData.tree.Insert(i + 1, value);
}

public int FindChildRecords(int id)
{
    var count = 0;
    for (var i = 0; i < TreeData.tree.Count; i++)
    {
        if (TreeData.tree[i].ParentItem == id)
        {
            count++;
            count += FindChildRecords(TreeData.tree[i].TaskID);
        }
    }
    return count;
}

```

The newly added record details are bound to the `value` parameter and `relationalKey` contains primaryKey value of an selected record helps to find out the position of newly added record. Please refer to the following screenshot.

![Insert](images/insert.PNG)

### Update record

Using the `updateUrl` property, the controller action mapping URL can be specified to perform save/update operation on the server-side.

The following code example describes the previous behavior.

```typescript

public ActionResult Update(TreeGridData value)
{
    var val = TreeData.tree.Where(ds => ds.TaskID == value.TaskID).FirstOrDefault();
    val.TaskName = value.TaskName;
    val.StartDate = value.StartDate;
    val.Duration = value.Duration;
    val.Priority = value.Priority;
    val.Progress = value.Progress;
    return Json(value);
}

```

The updated record details are bound to the `value` parameter. Please refer to the following screenshot.

![Update](images/update.PNG)

### Delete record

Using the `removeUrl` and `batchUrl` property, the controller action mapping URL can be specified to perform delete operation on the server-side.

The following code example describes the previous behavior.

```typescript

public ActionResult Delete(int key)
{
    TreeData.tree.Remove(TreeData.tree.Where(ds => ds.TaskID == key).FirstOrDefault());
}

// Remove method (batchUrl) will be triggered when we delete parent record.

public ActionResult Remove(List<TreeGridData> changed, List<TreeGridData> added, List<TreeGridData> deleted)
{
    for (var i = 0; i < deleted.Count; i++)
    {
        TreeData.tree.Remove(TreeData.tree.Where(ds => ds.TaskID == deleted[i].TaskID).FirstOrDefault());
    }
}

```

The deleted record primary key value is bound to the `key` parameter. Please refer to the following screenshot.

![Delete](images/remove.PNG)

While delete parent record, the parent and child records is bound to the `deleted` parameter. Please refer to the following screenshot.

![Remove](images/delete.PNG)

### Remote Save Adaptor

You may need to perform all Tree Grid Actions in client-side except the CRUD operations, that should be interacted with server-side to persist data. It can be achieved in TreeGrid by using **RemoteSaveAdaptor**.

Datasource must be set to **json** property and set **RemoteSaveAdaptor** to the **adaptor** property. CRUD operations can be mapped to server-side using **updateUrl**, **insertUrl**, **removeUrl** and **batchUrl** properties.

You can use the following code example to use **RemoteSaveAdaptor** in TreeGrid.

```typescript

import { TreeGrid, Edit, Toolbar } from '@syncfusion/ej2-treegrid';
import { DataManager, RemoteSaveAdaptor } from '@syncfusion/ej2-data';

TreeGrid.Inject(Edit, Toolbar);

let dataSource: DataManager = new DataManager({
    json: window.griddata,
    updateUrl: "Home/Update",
    insertUrl: "Home/Insert",
    removeUrl: "Home/Delete",
    batchUrl: "Home/Remove",
    adaptor: new RemoteSaveAdaptor
});

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: dataSource,
    idMapping: 'TaskID',
    parentIdMapping: 'parentItem',
    hasChildMapping: 'isParent',
    toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Row' },
    treeColumnIndex: 1,
    columns: [
        { field: 'TaskID', headerText: 'Task ID', isPrimaryKey: true, width: 90, textAlign: 'Right'},
        { field: 'TaskName', headerText: 'Task Name', width: 180 },
        {
            field: 'StartDate', headerText: 'Start Date', width: 90, textAlign: 'Right', editType: 'datepickeredit', type: 'date', format: 'yMd'
        },
        { field: 'Priority', headerText: 'Priority', width: 80, validationRules: { required: true } }
    ],
    height: 270
});
treeGridObj.appendTo('#TreeGrid');

```

The following code example describes how to fetch the data from `ViewBag` in angular.

```html
    <script type="text/javascript">
       window.griddata = '@Html.Raw(Json.Encode(ViewBag.dataSource))';
    </script>
```

The following code example describes the CRUD operations handled at server-side.

```typescript

public ActionResult Index(DataManager dm)
{
   var data = TreeData.GetTree();
   ViewBag.dataSource = data;
   return View();
}

public void Insert(TreeData value, int relationalKey)
{
    var i = 0;
    for (; i < TreeData.tree.Count; i++)
    {
        if (TreeData.tree[i].TaskID == relationalKey)
        {
            break;
        }
    }
    i += FindChildRecords(relationalKey); // Inserted new record when newRowPosition API is in "Below".
    TreeData.tree.Insert(i + 1, value);
}

public ActionResult Update(TreeData value)
{
    var val = TreeData.tree.Where(ds => ds.TaskID == value.TaskID).FirstOrDefault();
    val.TaskName = value.TaskName;
    val.StartDate = value.StartDate;
    val.Duration = value.Duration;
    val.Priority = value.Priority;
    val.Progress = value.Progress;
    return Json(value);
}

public ActionResult Delete(int key)
{
    TreeData.tree.Remove(TreeData.tree.Where(ds => ds.TaskID == key).FirstOrDefault());;
}

// Remove method (batchUrl) will be triggered when we delete parent record.

public ActionResult Remove(List<TreeGridData> changed, List<TreeGridData> added, List<TreeGridData> deleted)
{
    for (var i = 0; i < deleted.Count; i++)
    {
        TreeData.tree.Remove(TreeData.tree.Where(ds => ds.TaskID == deleted[i].TaskID).FirstOrDefault());
    }
}

```

## Default column values on add new

The treegrid provides an option to set the default value for the columns when adding a new record in it.
To set a default value for the particular column by defining the [`columns.defaultValue`](../api/treegrid/column/#defaultvalue).

{% tab template="treegrid/edit",es5Template="defaultvalue" %}

```typescript
import { TreeGrid, Edit, Toolbar } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Edit, Toolbar);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    toolbar: ['Add', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, showDeleteConfirmDialog: true, mode: 'Cell' },
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', isPrimaryKey: true, width: 90, textAlign: 'Right'},
        { field: 'taskName', headerText: 'Task Name', width: 180 },
        {
            field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', editType: 'datepickeredit', type: 'date', format: 'yMd'
        },
        { field: 'priority', headerText: 'Priority', width: 80, defaultValue: 'Normal' }
    ],
    height: 270
});
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Disable editing for particular column

You can disable editing for particular columns by using the [`columns.allowEditing`](../api/treegrid/column/#allowediting).

In the following demo, editing is disabled for the `Start Date` column.

{% tab template="treegrid/edit",es5Template="disableedit" %}

```typescript
import { TreeGrid, Edit, Toolbar } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Edit, Toolbar);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    toolbar: ['Add', 'Delete', 'Update', 'Cancel'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Cell' },
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', isPrimaryKey: true, width: 90, textAlign: 'Right'},
        { field: 'taskName', headerText: 'Task Name', width: 180 },
        {
            field: 'startDate', headerText: 'Start Date', width: 90, allowEditing: false, textAlign: 'Right', type: 'date', format: 'yMd'
        },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ],
    height: 270
});
treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Troubleshoot: Editing works only for first row

The Editing functionalities can be performed based upon the primary key value of the selected row.
If `primaryKey` is not defined in the treegrid, then edit or delete action take places the first row.

> You can refer to our [`JavaScript Tree Grid`](https://www.syncfusion.com/javascript-ui-controls/js-tree-grid) feature tour page for its groundbreaking feature representations. You can also explore our JavaScript Tree Grid example [`JavaScript Tree Grid example`](https://ej2.syncfusion.com/demos/#/material/tree-grid/treegrid-overview.html) to knows how to present and manipulate data.