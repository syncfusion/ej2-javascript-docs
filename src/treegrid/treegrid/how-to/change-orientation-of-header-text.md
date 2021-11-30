---
title: "Change the Orientation of Header Text"
component: "TreeGrid"
description: "Learn how to Change the Orientation of Header Text."
---

# Change the Orientation of Header Text

You can change the orientation of the header text by using the [`customAttributes`](../../api/treegrid/column/#customattributes) property.

Ensure the following steps:

**Step 1**:

Create a CSS class with orientation style for the treegrid header cell.

```css
.orientationcss .e-headercelldiv {
    transform: rotate(90deg);
}

```

**Step 2**:

Add the custom CSS class to a particular column by using the [`customAttributes`](../../api/treegrid/column/#customattributes) property.

```typescript
    { field: 'taskName', headerText: 'Task Name', textAlign: 'Center', customAttributes: {class: 'orientationcss'}, width: 80 }

```

**Step 3**:

Resize the header cell height by using the following code.

```typescript
function setHeaderHeight(args) {
    let textWidth: number = document.querySelector(".orientationcss > div").scrollWidth;//Obtain the width of the headerText content.
    let headerCell: NodeList = document.querySelectorAll(".e-headercell");
    for(let i: number = 0; i < headerCell.length; i++) {
        (<HTMLElement>headerCell.item(i)).style.height = textWidth + 'px'; //Assign the obtained textWidth as the height of the headerCell.
    }
}

```

{% tab template="treegrid/orientation", sourceFiles="index.ts,index.css",es5Template="headertext" %}

```typescript
import { TreeGrid,ActionEventArgs } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

    let treegrid: TreeGrid = new TreeGrid(
        {
            dataSource: sampleData,
            childMapping: "subtasks",
            treeColumnIndex: 1,
            height: 100,
            created: setHeaderHeight,
            columns: [
               { field: 'taskID', headerText: 'Task ID', width: 70, textAlign: 'Right' },
               { field: 'taskName', headerText: 'Task Name', textAlign: 'Center', customAttributes: {class: 'orientationcss'}, width: 80 }
               { field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd' },
               { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
            ]
            });
    treegrid.appendTo('#TreeGrid');

    function setHeaderHeight(args: ActionEventArgs): void {
   let textWidth: number = document.querySelector(".orientationcss > div").scrollWidth; // obtain the width of the headerText content.
    let headerCell: NodeList = document.querySelectorAll(".e-headercell");
    for (let i: number = 0; i < headerCell.length; i++) {
        (<HTMLElement>headerCell.item(i)).style.height = textWidth + 'px'; // assign the obtained textWidth as the height of the headerCell.
    }
}

```

{% endtab %}

> You can refer to our [`JavaScript Tree Grid`](https://www.syncfusion.com/javascript-ui-controls/js-tree-grid) feature tour page for its groundbreaking feature representations. You can also explore our JavaScript Tree Grid example [`JavaScript Tree Grid example`](https://ej2.syncfusion.com/demos/#/material/tree-grid/treegrid-overview.html) to knows how to present and manipulate data.