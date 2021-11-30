---
title: "Change column headerText dynamically"
component: "TreeGrid"
description: "Learn how to change column Header Text dynamically"
---

# Change column Header Text dynamically

You can change the column [`headerText`](../../api/treegrid/column/#headertext) dynamically through an external button.

Follow the given steps to change the header text dynamically:

**Step 1**:

Get the column object corresponding to the field name by using the [`getColumnByField`](../../api/treegrid/#getcolumnbyfield) method.
Then, change the header text value.

```typescript
let column = treegrid.getColumnByField("taskName"); // Get column object.
column.headerText = 'Changed Text';

```

**Step 2**:

To reflect the changes in the treegrid header, invoke the [`refreshColumns`](../../api/treegrid/#refreshcolumns) method.

```typescript

treegrid.refreshColumns();

```

{% tab template="treegrid/headertext", sourceFiles="index.ts,index.css,index.html",es5Template="headertext" %}

```typescript

import { TreeGrid, Page,Column } from '@syncfusion/ej2-treegrid';
import { Button } from '@syncfusion/ej2-buttons';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Page);

let button: Button = new Button();
button.appendTo("#change-text");

let treegrid: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    treeColumnIndex: 1,
     columns: [
     { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
     { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
     { field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'},
     { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ],
});
treegrid.appendTo('#TreeGrid');

document.getElementById("change-text").addEventListener("click", () => {
  let column = treegrid.getColumnByField("taskName"); // get the JSON object of the column corresponding to the field name.
  column.headerText = "Changed Text"; // assign a new header text to the column.
  treegrid.refreshColumns();
});

```

{% endtab %}

> You can refer to our [`JavaScript Tree Grid`](https://www.syncfusion.com/javascript-ui-controls/js-tree-grid) feature tour page for its groundbreaking feature representations. You can also explore our JavaScript Tree Grid example [`JavaScript Tree Grid example`](https://ej2.syncfusion.com/demos/#/material/tree-grid/treegrid-overview.html) to knows how to present and manipulate data.