---
title: "Refresh the data source"
component: "TreeGrid"
description: "Learn how to customize the Essential JS 2 Tree Grid."
---

# How To

## How to refresh the datasource

You can add/delete the datasource records through an external button. To reflect the datasource changes in Tree Grid, you need to assign the modified data to dataSource property.

Please follow the below steps to refresh the Tree Grid after datasource change.

**Step 1**:

Add/delete the data source record by using the following code.

```typescript
    treegrid.dataSource.unshift(data); // add a new record.

    treegrid.dataSource.splice(selectedRow, 1); // delete a record.

```

**Step 2**:

Refresh the Tree Grid after the data source change by using the [`refresh`](../../api/treegrid/#refresh) method.

```typescript
    treegrid.refresh(); // refresh the Grid.

```

{% tab template="treegrid/refresh", sourceFiles="index.ts,index.css,index.html",es5Template="refresh" %}

```typescript

import { TreeGrid ,extendArray} from '@syncfusion/ej2-treegrid';
import { Button } from '@syncfusion/ej2-buttons';
import { projectData } from './datasource.ts';

let treegrid: TreeGrid = new TreeGrid({
    dataSource: projectData,
    idMapping: 'TaskID',
    parentIdMapping: 'parentID',
    treeColumnIndex: 1,
     columns: [
     { field: 'TaskID', headerText: 'Task ID', width: 70, textAlign: 'Right' },
     { field: 'TaskName', headerText: 'Task Name', width: 100, textAlign: 'Left' },
     { field: 'StartDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'},
     { field: 'EndDate', headerText: 'End Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'},
     { field: 'Duration', headerText: 'Duration', width: 90, textAlign: 'Right' },
     { field: 'Priority', headerText: 'Priority', width: 90, textAlign: 'Right' }
    ],
});
treegrid.appendTo('#TreeGrid');

let add: Button = new Button({}, '#add');
let dele: Button = new Button({}, '#delete');

document.getElementById('add').onclick = () => {
 let treegrid = document.getElementsByClassName("e-treegrid")[0].ej2_instances[0];   //take treegrid instance here
     let dataSource = extendArray(treegrid.dataSource);
     dataSource.unshift({ TaskID: 99, TaskName: "New Data", StartDate: new Date('09/07/2020'), Duration: 10, Priority: "High" }); // Add record
        treegrid.dataSource = dataSource;  // Refresh the TreeGrid.
};

document.getElementById('delete').onclick = () => {
    let treegrid = document.getElementsByClassName("e-treegrid")[0].ej2_instances[0]; //take treegrid instance here
    let selectedRow = treegrid.getSelectedRowIndexes().length;
     let selectedRowIndex = treegrid.getSelectedRowIndexes()[0];
        let dataSource = extendArray(treegrid.dataSource);
        if (selectedRow > 0) {
            dataSource.splice(selectedRowIndex, 1); // Delete record.
        }
        else {
            alert("No records selected for delete operation");
            }
        treegrid.dataSource = dataSource; // Refresh the TreeGrid.
};

```

{% endtab %}