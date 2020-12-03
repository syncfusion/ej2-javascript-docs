---
title: "Search"
component: "TreeGrid"
description: "Learn how to search TreeGrid content, change search operators, perform searches using external buttons, and search particular fields."
---

# Search

You can search records in a TreeGrid, by using the [`search`](../api/treegrid/#search) method with search key as a parameter. This also provides an option to integrate search text box in treegrid's toolbar by adding `search` item to the [`toolbar`](../api/treegrid/#toolbar).

To search records, inject the [`Filter`](../api/treegrid/#fitermodule) module in the treegrid.

{% tab template="treegrid/searching", es5Template="search" %}

```typescript
import { TreeGrid, Filter, Toolbar } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Filter, Toolbar);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    toolbar: ['Search'],
    height: 270,
    treeColumnIndex: 1,
    columns: [
                { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 180 },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
                { field: 'progress', headerText: 'progress', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

## Initial search

To apply search at initial rendering, set the fields, operator, key, and ignoreCase in the [`searchSettings`](../api/treegrid/#searchsettings).

{% tab template="treegrid/searching", es5Template="initsearch" %}

```typescript
import { TreeGrid, Filter, Toolbar } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Filter, Toolbar);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    toolbar: ['Search'],
    searchSettings: { fields: ['taskName'], operator: 'contains', key: 'plan', ignoreCase: true },
    height: 270,
    treeColumnIndex: 1,
    columns: [
                { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 180 },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
                { field: 'progress', headerText: 'progress', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

> By default, treegrid searches all the bound column values. To customize this behavior define the [`searchSettings.fields`](../api/treegrid/searchSettingsModel/#fields) property.

## Search operators

The search operator can be defined in the [`searchSettings.operator`](../api/treegrid/searchSettingsModel/#operator) property to configure specific searching.

The following operators are supported in searching:

Operator |Description
-----|-----
startsWith |Checks whether a value begins with the specified value.
endsWith |Checks whether a value ends with the specified value.
contains |Checks whether a value contains the specified value.
equal |Checks whether a value is equal to the specified value.
notEqual |Checks for values not equal to the specified value.

> By default, the [`searchSettings.operator`](../api/treegrid/searchSettingsModel/#operator) value is `contains`.

## Search by external button

To search treegrid records from an external button, invoke the [`search`](../api/treegrid/#search) method.

{% tab template="treegrid/search-method", es5Template="external" %}

```typescript
import { TreeGrid, Filter } from '@syncfusion/ej2-treegrid';
import { Button } from '@syncfusion/ej2-buttons';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Filter);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    height: 220,
    treeColumnIndex: 1,
    columns: [
                { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 180 },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
                { field: 'progress', headerText: 'progress', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

let searchBtn: Button = new Button();
searchBtn.appendTo('#search');

document.getElementById('search').addEventListener('click', () => {
    let searchText: string = (<HTMLInputElement>document.getElementsByClassName('searchtext')[0]).value;
    treeGridObj.search(searchText);
});

```

{% endtab %}

## Search specific columns

By default, treegrid searches all visible columns. You can search specific columns by defining the specific column's field names in the [`searchSettings.fields`](../api/treegrid/searchSettingsModel/#fields) property.

{% tab template="treegrid/searching", es5Template="specific" %}

```typescript
import { TreeGrid, Filter, Toolbar } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Filter, Toolbar);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    toolbar: ['Search'],
    searchSettings: { fields: ['taskName', 'duration']},
    height: 270,
    treeColumnIndex: 1,
    columns: [
                { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 180 },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
                { field: 'progress', headerText: 'progress', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}