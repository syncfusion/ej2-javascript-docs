---
title: "Filtering"
component: "TreeGrid"
description: "Learn how to filter rows in the TreeGrid using the filter bar, menu, excel and checkbox filtering. Also learn how to use custom filter components in the Essential JS 2 TreeGrid control."
---

# Filtering

Filtering allows you to view specific or related records based on filter criteria. To enable filtering in the TreeGrid, set the [`allowFiltering`](../api/treegrid/#allowfiltering) to true. Filtering options can be configured through [`filterSettings`](../api/treegrid/#filtersettings).

To use filter, inject the `Filter` module in the treegrid.

{% tab template="treegrid/filtering",es5Template="filter" %}

```typescript
import { TreeGrid, Filter } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Filter);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 275,
    allowFiltering: true,
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', width: 75, textAlign: 'Right' },
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

> * You can apply and clear filtering by using [`filterByColumn`](../api/treegrid/#filterbycolumn) and [`clearFiltering`](../api/treegrid/#clearfiltering) methods.
> * To disable filtering for a particular column, set
[`columns.allowFiltering`](../api/treegrid/column/#allowfiltering) to false.

## Filter Hierarchy Modes

TreeGrid provides support for a set of filtering modes with [`filterSettings.filterHierarchyMode`](../api/treegrid/filterSettingsModel/#hierarchymode) property.
The below are the type of filter mode available in TreeGrid.

* **Parent** : This is the default filter hierarchy mode in TreeGrid. The filtered records are displayed with its parent records, if the filtered records not have any parent record then the filtered records only displayed.

* **Child** : The filtered records are displayed with its child record, if the filtered records not have any child record then the filtered records only displayed.

* **Both** : The filtered records are displayed with its both parent and child record, if the filtered records not have any parent and child record then the filtered records only displayed.

* **None** : The filtered records are only displayed.

{% tab template="treegrid/hierarchy-filtering",es5Template="hierarchy" %}

```typescript
import { TreeGrid, Filter } from '@syncfusion/ej2-treegrid';
import { DropDownList, ChangeEventArgs } from '@syncfusion/ej2-dropdowns';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Filter);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 225,
    allowFiltering: true,
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', width: 75, textAlign: 'Right' },
        { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
        {
            field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
        },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

 let dropDownMode: DropDownList = new DropDownList({
    dataSource: [
        { id: 'Parent', mode: 'Parent' },
        { id: 'Child', mode: 'Child' },
        { id: 'Both', mode: 'Both' },
        { id: 'None', mode: 'None' },
    ],
    fields: { text: 'mode', value: 'id' },
    value: 'Parent',
    change: (e: ChangeEventArgs) => {
        let mode: any = <string>e.value;
        treeGridObj.filterSettings.hierarchyMode = mode;
        treeGridObj.clearFiltering();
    }
});
dropDownMode.appendTo('#mode');

```

{% endtab %}

## Initial filter

To apply the filter at initial rendering, set the filter `predicate` object in
[`filterSettings.columns`](../api/treegrid/filterSettingsModel/#columns).

{% tab template="treegrid/filtering",es5Template="initfilter" %}

```typescript
import { TreeGrid, Filter } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Filter);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 275,
    allowFiltering: true,
     filterSettings: {
        columns: [{ field: 'taskName', matchCase: false, operator: 'startswith', predicate: 'and', value: 'plan' },
        { field: 'duration', matchCase: false, operator: 'equal', predicate: 'and', value: 5 }]
    },
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', width: 75, textAlign: 'Right' },
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

## Filter operators

The filter operator for a column can be defined in the `filterSettings.columns.operator` property.

The available operators and its supported data types are:

Operator |Description |Supported Types
-----|-----|-----
startswith |Checks whether the value begins with the specified value. |String
endswith |Checks whether the value ends with the specified value. |String
contains |Checks whether the value contains the specified value. |String
equal |Checks whether the value is equal to the specified value. |String &#124; Number &#124; Boolean &#124; Date
notequal |Checks for values not equal to the specified value. |String &#124; Number &#124; Boolean &#124; Date
greaterthan |Checks whether the value is greater than the specified value. |Number &#124; Date
greaterthanorequal|Checks whether a value is greater than or equal to the specified value. |Number &#124; Date
lessthan |Checks whether the value is less than the specified value. |Number &#124; Date
lessthanorequal |Checks whether the value is less than or equal to the specified value. |Number &#124; Date

> By default, the `filterSettings.columns.operator` value is `equal`.

## Filter bar

By setting the [`allowFiltering`](../api/treegrid/#allowfiltering) to true, the filter bar row will render next to the header, which allows you to filter data. You can filter the records with different expressions depending upon the column type.

 **Filter bar expressions:**

 You can enter the following filter expressions (operators) manually in the filter bar.

Expression |Example |Description |Column Type
-----|-----|-----|-----
= |=value |equal |Number
!= |!=value |notequal |Number
> |>value |greaterthan |Number
< |<value |lessthan |Number
>= |>=value |greaterthanorequal |Number
<=|<=value|lessthanorequal |Number
* |*value |startswith |String
% |%value |endswith |String
N/A |N/A | `Equal` operator will always be used for date filter. |Date
N/A |N/A |`Equal` operator will always be used for Boolean filter. |Boolean

{% tab template="treegrid/filtering",es5Template="filterbar" %}

```typescript
import { TreeGrid, Filter } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Filter);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 275,
    allowFiltering: true,
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', width: 75, textAlign: 'Right' },
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

### Filter bar template with custom component

The [`filterBarTemplate`](../api/treegrid/column/#filterbartemplate) is used to add custom components to a particular column, and does the following functions:
* `create`: Creates custom components.
* `write`: Wires events for custom components.

In the following sample, the dropdown is used as a custom component in the Duration column.

{% tab template="treegrid/filtering", es5Template="custom" %}

```typescript
import { TreeGrid, Filter, Column } from '@syncfusion/ej2-treegrid';
import { DropDownList, ChangeEventArgs } from '@syncfusion/ej2-dropdowns';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Filter);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 275,
    allowFiltering: true,
    filterSettings: { type: 'FilterBar', hierarchyMode: 'Parent', mode: 'Immediate' },
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', width: 75, textAlign: 'Right' },
        { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
        {
            field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
        },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right',
          filterBarTemplate: {
                create: (args: { element: Element, column: Column }) => {
                    let dd: HTMLInputElement = document.createElement('input');
                    dd.id = 'duration';
                    return dd;
                },
                write: (args: { element: Element, column: Column }) => {
                    let dataSource: string[] = ['All', '1', '3', '4', '5', '6', '8', '9'];
                    this.dropDownFilter = new DropDownList({
                        dataSource: dataSource,
                        value: 'All',
                        change: (e: ChangeEventArgs) => {
                            let valuenum: any = +e.value;
                            let id: any = <string>this.dropDownFilter.element.id;
                            let value: any = <string>e.value;
                            if ( value !== 'All') {
                                treeGridObj.filterByColumn( id, 'equal', valuenum );
                            } else {
                                treeGridObj.removeFilteredColsByField(id);
                            }
                        }
                    });
                    this.dropDownFilter.appendTo('#duration');
                }
            }
        }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

### Change default filter bar operator

You can change the default filter operator by extending [`filterModule.filterOperators`](../api/treegrid/filterSettings/#operators) property in [`dataBound`](../api/treegrid/#databound) event.

In the following sample, we have changed the default operator for string typed columns as `contains` from `startsWith`.

{% tab template="treegrid/filtering",es5Template="Default filterbar" %}

```typescript
import { TreeGrid, Filter, Column } from '@syncfusion/ej2-treegrid';
import { DropDownList, ChangeEventArgs } from '@syncfusion/ej2-dropdowns';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Filter);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    dataBound: dataBound,
    allowFiltering: true,
    filterSettings: { type: 'FilterBar', hierarchyMode: 'Parent', mode: 'Immediate' },
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', width: 75, textAlign: 'Right' },
        { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
        {
            field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
        },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

function dataBound(): void {
         Object.assign(treeGridObj.grid.filterModule.filterOperators, { startsWith: 'contains' });
}

```

{% endtab %}

## Filter menu

You can enable filter menu by setting the [`filterSettings.type`](../api/treegrid/filterSettingsModel/#type) as `Menu`. The filter menu UI will be rendered based on its column type, which allows you to filter data.
You can filter the records with different operators.

{% tab template="treegrid/filtering",es5Template="filtermenu" %}

```typescript
import { TreeGrid, Filter } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Filter);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 275,
    allowFiltering: true,
    filterSettings: {type: 'Menu'},
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', width: 75, textAlign: 'Right' },
        { field: 'taskName', headerText: 'Task Name', width: 120, textAlign: 'Left' },
        {
            field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
        }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

> * [`allowFiltering`](../api/treegrid/#allowfiltering) must be set as true to enable filter menu.
> * Setting [`columns.allowFiltering`](../api/treegrid/column/#allowfiltering) as false will prevent filter menu rendering for a particular column.

### Custom component in filter menu

The [`column.filter.ui`](../api/treegrid/column/#filter) is used to add custom filter components to a particular column. To implement custom filter ui, define the following functions:

* `create`:  Creates custom component.
* `write`: Wire events for custom component.
* `read`: Read the filter value from custom component.

In the following sample, dropdown is used  as custom component in the duration column.

{% tab template="treegrid/filtering",es5Template="customfiltermenu" %}

```typescript
import { TreeGrid, Filter } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';
import { DataManager } from '@syncfusion/ej2-data';
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { createElement } from '@syncfusion/ej2-base';

TreeGrid.Inject(Filter);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 275,
    allowFiltering: true,
    filterSettings: {type: 'Menu'},
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 75, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 120, textAlign: 'Left' },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right', filter: {
                ui: {
                    create: (args: { target: Element, column: Object }) => {
                        let flValInput: HTMLElement = createElement('input', { className: 'flm-input' });
                        args.target.appendChild(flValInput);
                        let dataSource: string[] = ['All', '1', '3', '4', '5', '6', '8', '9'];
                        this.dropDownFilter = new DropDownList({
                            dataSource: dataSource,
                            value: 'All', popupHeight: '200px'
                        });
                        this.dropDownFilter.appendTo(flValInput);
                    },
                    write: (args: {
                        column: Object, target: Element, parent: any,
                        filteredValue: number | string
                    }) => {
                        this.dropDownFilter.value = args.filteredValue;
                    },
                    read: (args: { target: Element, column: any, operator: string, fltrObj: Filter }) => {
                        args.fltrObj.filterByColumn(args.column.field, args.operator, parseInt(this.dropDownFilter.value));

                    }
                }}
            }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

### Enable different filter for a column

You can use both `Menu` and `Excel` filter in a same TreeGrid. To do so, set the
[`column.filter.type`](../api/treegrid/column/#filter) as `Menu` or `Excel`.

In the following sample menu filter is enabled by default and excel filter is enabled for the Task Name column using the
[`column.filter.type`](../api/treegrid/column/#filter).

{% tab template="treegrid/filtering",es5Template="filtercolumn" %}

```typescript
import { TreeGrid, Filter } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Filter);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 273,
    allowFiltering: true,
    filterSettings: { type:'Menu' },
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', width: 75, textAlign: 'Right' },
        { field: 'taskName', headerText: 'Task Name', width: 150, textAlign: 'Left', filter: { type : 'Excel' } },
        { field: 'duration', headerText: 'Duration', width: 90, textAlign: 'Right' },
        { field: 'progress', headerText: 'Progress', width: 90, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Excel like filter

You can enable Excel like filter by defining.
[`filterSettings.type`](../api/treegrid/filterSettingsModel/#type) as `Excel`.The excel menu contains an option such as Sorting, Clear filter, Sub menu for advanced filtering.

{% tab template="treegrid/filtering",es5Template="excelfilter" %}

```typescript
import { TreeGrid, Filter } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Filter);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 273,
    allowFiltering: true,
    filterSettings: { type:'Excel' },
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', width: 75, textAlign: 'Right' },
        { field: 'taskName', headerText: 'Task Name', width: 150, textAlign: 'Left' },
        { field: 'duration', headerText: 'Duration', width: 90, textAlign: 'Right' },
        { field: 'progress', headerText: 'Progress', width: 90, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

### Change default Excel filter operator

You can change the default excel-filter operator by changing the column operator as `contains` from `startsWith` in the [`actionBegin`](../api/treegrid/#actionBegin) event

{% tab template="treegrid/filtering",es5Template="excelfilter" %}

```typescript

import { TreeGrid, Filter, Column } from '@syncfusion/ej2-treegrid';
import { DropDownList, ChangeEventArgs } from '@syncfusion/ej2-dropdowns';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Filter);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    actionBegin:actionBegin,
    allowFiltering: true,
    filterSettings: { type: 'Excel'},
    treeColumnIndex: 1,
    columns: [
        { field: 'taskID', headerText: 'Task ID', width: 75, textAlign: 'Right' },
        { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
        {
            field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
        },
        { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

function actionBegin(e) {
    if(e.requestType === 'filtersearchbegin' && e.column.type === "string")
       {
        e.operator = 'contains';
       }
}

```

{% endtab %}

## Diacritics

By default, treegrid ignores diacritic characters while filtering. To include diacritic characters, set the
[`filterSettings.ignoreAccent`](../api/treegrid/filterSettingsModel/#ignoreaccent) as `true`.

In the following sample, type **aero** in `Name` column to filter diacritic characters.

{% tab template="treegrid/filtering",es5Template="diacritics" %}

```typescript
import { TreeGrid, Filter } from '@syncfusion/ej2-treegrid';
import { diacritics } from './datasource.ts';

TreeGrid.Inject(Filter);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: diacritics,
    childMapping: 'Children',
    height: 275,
    allowFiltering: true,
    filterSettings: { ignoreAccent: true },
    treeColumnIndex: 0,
    columns: [
        { field: 'EmpID', headerText: 'Employee ID', width: 95 },
        { field: 'Name', headerText: 'Name', width: 110 },
        { field: 'DOB', headerText: 'DOB', width: 90, textAlign: 'Right', format: 'yMd' },
        { field: 'Country', width: 65 }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}