---
title: "Adaptive"
component: "Grid"
description: "Learn how to render the row elements, filter, sort, and edit dialogs adaptively in the Essential JS 2 DataGrid control."
---

# Adaptive View

The Grid user interface (UI) was redesigned to provide an optimal viewing experience and improve usability on small screens. This interface will render the filter, sort, and edit dialogs adaptively and have an option to render the grid row elements in the vertical direction.

## Render adaptive dialogs

When we enable the [`enableAdaptiveUI`](../api/grid/#enableadaptiveui) property, the grid will render the filter, sort, and edit dialogs in full screen for a better user experience. This behavior is demonstrated in the below demo.

{% tab template="grid/adaptive",es5Template="control" %}

```typescript
import { Grid, Filter, Sort, Edit, Toolbar, Page } from '@syncfusion/ej2-grids';
import { Browser } from '@syncfusion/ej2-base';
import { data } from './datasource.ts';

Grid.Inject(Filter, Sort, Edit, Toolbar, Page);

let grid: Grid = new Grid({
    dataSource: data,
    enableAdaptiveUI: true,
    allowPaging: true,
    allowSorting: true,
    allowFiltering: true,
    filterSettings: { type: 'Excel' },
    toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel', 'Search'],
    editSettings: { allowAdding: true, allowEditing: true, allowDeleting: true, mode: 'Dialog' },
    height: '100%',
    load: () => {
        grid.adaptiveDlgTarget = document.getElementsByClassName('e-mobile-content')[0] as HTMLElement;
    },
    columns: [
        { field: 'SNO', headerText: 'S NO', isPrimaryKey: true, width: 150, validationRules: { required: true, number: true } },
        { field: 'Model', headerText: 'Model Name', width: 200, editType: "dropdownedit", validationRules: { required: true } },
        { field: 'Developer', headerText: 'Developer', filter: { type : 'Menu' }, width: 200, validationRules: { required: true } },
        { field: 'ReleaseDate', headerText: 'Released Date', type: 'date', editType: "datepickeredit", format: 'yMMM', width: 200 },
        { field: 'AndroidVersion', headerText: 'Android Version', filter: { type : 'CheckBox' }, width: 200, validationRules: { required: true } }
    ]
});
grid.appendTo('#adaptivebrowser');

```

{% endtab %}

## Vertical row rendering

The grid will render the row elements in vertical order while setting the [`rowRenderingMode`](../api/grid/rowRenderingMode) property value as **Vertical**.

{% tab template="grid/vertical-rendering",es5Template="control" %}

```typescript
import { Grid, Filter, Sort, Edit, Toolbar, Aggregate, Page } from '@syncfusion/ej2-grids';
import { Browser } from '@syncfusion/ej2-base';
import { data } from './datasource.ts';

Grid.Inject(Filter, Sort, Edit, Toolbar, Aggregate, Page);

let grid: Grid = new Grid({
    dataSource: data,
    enableAdaptiveUI: true,
    rowRenderingMode: 'Vertical',
    allowPaging: true,
    allowSorting: true,
    allowFiltering: true,
    filterSettings: { type: 'Excel' },
    toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel', 'Search'],
    editSettings: { allowAdding: true, allowEditing: true, allowDeleting: true, mode: 'Dialog' },
    height: '100%',
    load: () => {
        grid.adaptiveDlgTarget = document.getElementsByClassName('e-mobile-content')[0] as HTMLElement;
    },
    columns: [
        { field: 'SNO', headerText: 'S NO', isPrimaryKey: true, width: 150, validationRules: { required: true, number: true } },
        { field: 'Model', headerText: 'Model Name', width: 200, editType: "dropdownedit", validationRules: { required: true } },
        { field: 'Developer', headerText: 'Developer', filter: { type : 'Menu' }, width: 200, validationRules: { required: true } },
        { field: 'ReleaseDate', headerText: 'Released Date', type: 'date', editType: "datepickeredit", format: 'yMMM', width: 200 },
        { field: 'AndroidVersion', headerText: 'Android Version', filter: { type : 'CheckBox' }, width: 200, validationRules: { required: true } }
    ],
    aggregates: [{
        columns: [{
            type: 'Count',
            field: 'Model',
            footerTemplate: 'Total Models: ${Count}'
        }]
    }]
});
grid.appendTo('#verticalrender');

```

{% endtab %}

> * [`enableAdaptiveUI`](../api/grid/#enableadaptiveui) property must be enabled for vertical row rendering.

### Supported features by vertical row rendering

The following features are only supported in vertical row rendering:

* Paging
* Sorting
* Filtering
* Selection
* Dialog Editing
* Aggregate
* Infinite scroll
* Toolbar
