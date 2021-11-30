---
title: "Customize Column Styles"
component: "TreeGrid"
description: "Learn how to Customize Column Styles."
---

# Customize Column Styles

You can customise the appearance of the header and content of a particular column using the [`customAttributes`](../../api/treegrid/column/#customattributes) property.

To customize the Tree Grid column, follow the given steps:

**Step 1**:

Create a CSS class with custom style to override the default style for rowcell and header cell.

```css
.e-treegrid .e-rowcell.customcss{
    background-color: #ecedee;
    color: 'red';
    font-family: 'Bell MT';
    font-size: 20px;
}

.e-treegrid .e-headercell.customcss{
    background-color: #2382c3;
    color: white;
    font-family: 'Bell MT';
    font-size: 20px;
}

```

**Step 2**:

Add the custom CSS class to the specified column by using the [`customAttributes`](../../api/treegrid/column/#customattributes) property.

```typescript
{ field: 'taskName', headerText: 'Task Name', customAttributes: {class: 'customcss'}, width: 100 },

```

{% tab template="treegrid/columnstyle", sourceFiles="index.ts,index.css",es5Template="columnstyles" %}

```typescript

import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';


    let treegrid: TreeGrid = new TreeGrid(
        {
            dataSource: sampleData,
            childMapping: 'subtasks',
            treeColumnIndex: 1,
            columns: [
                { field: 'taskID', headerText: 'Task ID', width: 70, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 200,customAttributes: { class: 'customcss' },  textAlign: 'Left' },
                { field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd' },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' },

            ]
        });
    treegrid.appendTo('#TreeGrid');


```

{% endtab %}

> You can refer to our [`JavaScript Tree Grid`](https://www.syncfusion.com/javascript-ui-controls/js-tree-grid) feature tour page for its groundbreaking feature representations. You can also explore our JavaScript Tree Grid example [`JavaScript Tree Grid example`](https://ej2.syncfusion.com/demos/#/material/tree-grid/treegrid-overview.html) to knows how to present and manipulate data.
