---
title: "Virtualization"
component: "TreeGrid"
description: "Learn how to improve performance in the Essential JS 2 TreeGrid control by using row with virtualization. Also learn about the limitations of virtualization."
---

# Virtualization

TreeGrid allows you to load large amount of data without performance degradation.

To use virtualization, you need to inject `VirtualScroll` module in treegrid.

## Row Virtualization

Row virtualization allows you to load and render rows only in the content viewport. It is an alternative way of paging in which the rows will be appended while scrolling vertically. To setup the row virtualization, you need to define
[`enableVirtualization`](../api/treegrid/#enablevirtualization) as true and content height by [`height`](../api/treegrid/#height) property.

The number of records displayed in the TreeGrid is determined implicitly by height of the content area and a buffer records will be maintained in the TreeGrid content in addition to the original set of rows.

Expand and Collapse state of any child record will be persisted.

{% tab template="treegrid/virtualscroll", sourceFiles="index.ts,index.css,index.html",es5Template="virtualscroll" %}

```typescript
import { VirtualScroll, TreeGrid } from '@syncfusion/ej2-treegrid';
import { virtualData, dataSource } from './datasource.ts';

TreeGrid.Inject(VirtualScroll);

dataSource();

let treegrid: TreeGrid = new TreeGrid(
        {
            dataSource: virtualData,
            enableVirtualization: true,
            treeColumnIndex: 1,
            childMapping: 'Crew',
            height: 317,
            columns: [
                { field: 'TaskID', headerText: 'Player Jersey', width: 140, textAlign: 'Right' },
                { field: 'FIELD1', headerText: 'Player Name', width: 140 },
                { field: 'FIELD2', headerText: 'Year', width: 120, textAlign: 'Right' },
                { field: 'FIELD3', headerText: 'Stint', width: 120, textAlign: 'Right' },
                { field: 'FIELD4', headerText: 'TMID', width: 120, textAlign: 'Right' }
               ]
        });
    treegrid.appendTo('#TreeGrid');

```

{% endtab %}

## Limitations for Virtualization

* Due to the element height limitation in browsers, the maximum number of records loaded by the treegrid is limited by the browser capability.
* Cell selection will not be persisted in row.
* The page size provided must be two times larger than the number of visible rows in the grid. If the page size is failed to meet this condition then the size will be determined by TreeGrid.
* The virtual height of the treegrid content is calculated using the row height and total number of records in the data source and hence features which changes row height such as text wrapping are not supported. If you want to increase the row height to accommodate the content then you can specify the row height as below to ensure all the table rows are in same height.

```css
.e-treegrid .e-row {
    height: 2em;
}
```

* Programmatic selection using the **selectRows** method is not supported in virtual scrolling.
* Virtual scrolling is not compatible with Batch editing, detail template and Frozen columns.

> You can refer to our [`JavaScript Tree Grid`](https://www.syncfusion.com/javascript-ui-controls/js-tree-grid) feature tour page for its groundbreaking feature representations. You can also explore our JavaScript Tree Grid example [`JavaScript Tree Grid example`](https://ej2.syncfusion.com/demos/#/material/tree-grid/treegrid-overview.html) to knows how to present and manipulate data.