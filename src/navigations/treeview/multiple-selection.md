---
title: "Multi Selection"
component: "TreeView"
description: "Multiple node selection in treeview"
---

# Multi Selection

Selection provides an interactive support and highlights the node that you select. Selection can be done through simple mouse down or keyboard interaction.

The TreeView also supports selection of multiple nodes by setting [allowMultiSelection](../api/treeview#allowmultiselection) to **true**.

To multi-select, press and hold **CTRL** key and click the desired nodes. To select range of nodes, press and hold the **SHIFT** key and click the nodes.
In the following example, the `allowMultiSelection` property is enabled.

> Multi selection is not applicable through touch interactions.

{% tab template="treeview/multi-selection/selection", sourceFiles="index.ts,index.html", es5Template="treeview-multi-selection-template" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);
import { TreeView } from '@syncfusion/ej2-navigations';

let countries: { [key: string]: Object }[] = [
    { id: 1, name: 'Australia', hasChild: true, expanded: true },
    { id: 2, pid: 1, name: 'New South Wales', isSelected: true },
    { id: 3, pid: 1, name: 'Victoria' },
    { id: 4, pid: 1, name: 'South Australia' },
    { id: 6, pid: 1, name: 'Western Australia', isSelected: true },
    { id: 7, name: 'Brazil', hasChild: true },
    { id: 8, pid: 7, name: 'Paraná' },
    { id: 9, pid: 7, name: 'Ceará' },
    { id: 10, pid: 7, name: 'Acre' },
    { id: 11, name: 'China', hasChild: true },
    { id: 12, pid: 11, name: 'Guangzhou' },
    { id: 13, pid: 11, name: 'Shanghai' },
    { id: 14, pid: 11, name: 'Beijing' },
    { id: 15, pid: 11, name: 'Shantou' },
    { id: 16, name: 'France', hasChild: true },
    { id: 17, pid: 16, name: 'Pays de la Loire' },
    { id: 18, pid: 16, name: 'Aquitaine' },
    { id: 19, pid: 16, name: 'Brittany' },
    { id: 20, pid: 16, name: 'Lorraine' },
    { id: 21, name: 'India', hasChild: true },
    { id: 22, pid: 21, name: 'Assam' },
    { id: 23, pid: 21, name: 'Bihar' },
    { id: 24, pid: 21, name: 'Tamil Nadu' },
    { id: 25, pid: 21, name: 'Punjab' }
];

let treeObj: TreeView = new TreeView({
    fields: { dataSource: countries, id: 'id', parentID: 'pid', text: 'name', hasChildren: 'hasChild', selected: 'isSelected' },
    allowMultiSelection: true,
});
treeObj.appendTo('#tree');


```

{% endtab %}

## Selected nodes

You can get or set the selected nodes in TreeView at initial rendering and dynamically by using the [selectedNodes](../api/treeview#selectednodes) property. It will return the selected node’s ID as an array.

* The [`nodeselecting`](../api/treeview#nodeselecting) event is triggered before a node is selected/unselected which can be used to prevent the selection.

* The [`nodeSelected`](../api/treeview#nodeselected) event is triggered once a node is successfully selected/unselected.

In the following example, **New South Wales** and **Western Australia** nodes are selected at initial rendering. When a node is selected, the selected node’s ID is displayed in alert.

{% tab template="treeview/multi-selection/selected-nodes", sourceFiles="index.ts,index.html", es5Template="treeview-multi-nodes-template" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);
import { TreeView, NodeSelectEventArgs } from '@syncfusion/ej2-navigations';

let countries: { [key: string]: Object }[] = [
    { id: 1, name: 'Australia', hasChild: true, expanded: true },
    { id: 2, pid: 1, name: 'New South Wales', isSelected: true },
    { id: 3, pid: 1, name: 'Victoria' },
    { id: 4, pid: 1, name: 'South Australia' },
    { id: 6, pid: 1, name: 'Western Australia', isSelected: true },
    { id: 7, name: 'Brazil', hasChild: true },
    { id: 8, pid: 7, name: 'Paraná' },
    { id: 9, pid: 7, name: 'Ceará' },
    { id: 10, pid: 7, name: 'Acre' },
    { id: 11, name: 'China', hasChild: true },
    { id: 12, pid: 11, name: 'Guangzhou' },
    { id: 13, pid: 11, name: 'Shanghai' },
    { id: 14, pid: 11, name: 'Beijing' },
    { id: 15, pid: 11, name: 'Shantou' },
    { id: 16, name: 'France', hasChild: true },
    { id: 17, pid: 16, name: 'Pays de la Loire' },
    { id: 18, pid: 16, name: 'Aquitaine' },
    { id: 19, pid: 16, name: 'Brittany' },
    { id: 20, pid: 16, name: 'Lorraine' },
    { id: 21, name: 'India', hasChild: true },
    { id: 22, pid: 21, name: 'Assam' },
    { id: 23, pid: 21, name: 'Bihar' },
    { id: 24, pid: 21, name: 'Tamil Nadu' },
    { id: 25, pid: 21, name: 'Punjab' }
];

let treeObj: TreeView = new TreeView({
    fields: { dataSource: countries, id: 'id', parentID: 'pid', text: 'name', hasChildren: 'hasChild' },
    allowMultiSelection: true,
    selectedNodes: ['2','6'],
    nodeSelected: nodeSelected
});
treeObj.appendTo('#tree');

function nodeSelected(args: NodeSelectEventArgs) {
    alert("The selected node's id: " + treeObj.selectedNodes); // To alert the selected node's id.
}

```

{% endtab %}