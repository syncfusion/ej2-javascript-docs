# Disable the checkbox of the TreeView Nodes

You can disable the check box alone in TreeView instead of disabling the whole node. You need to include the `e-checkbox-disabled` class into the check box element using the `drawNode` event. Please refer to the following sample to disable the check box of the tree nodes.

{% tab template="treeview/how-to/disable-checkbox", sourceFiles="index.ts,index.html,index.css", es5Template="treeview-disable-checkbox-template" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
import { TreeView } from '@syncfusion/ej2-navigations';
enableRipple(true);

/**
 * Treeview Disable check box of parent nodes sample
 */

    // List data source for TreeView component
   let countries: { [key: string]: Object }[] = [
    { id: 1, name: 'India', hasChild: true, expanded: true },
    { id: 2, pid: 1, name: 'Assam' },
    { id: 3, pid: 1, name: 'Bihar' },
    { id: 4, pid: 1, name: 'Tamil Nadu' },
    { id: 6, pid: 1, name: 'Punjab' },
    { id: 7, name: 'Brazil', hasChild: true },
    { id: 8, pid: 7, name: 'Paraná' },
    { id: 9, pid: 7, name: 'Ceará' },
    { id: 10, pid: 7, name: 'Acre' },
    { id: 11, name: 'France', hasChild: true },
    { id: 12, pid: 11, name: 'Pays de la Loire' },
    { id: 13, pid: 11, name: 'Aquitaine' },
    { id: 14, pid: 11, name: 'Brittany' },
    { id: 15, pid: 11, name: 'Lorraine' },
    { id: 16, name: 'Australia', hasChild: true },
    { id: 17, pid: 16, name: 'New South Wales' },
    { id: 18, pid: 16, name: 'Victoria' },
    { id: 19, pid: 16, name: 'South Australia' },
    { id: 20, pid: 16, name: 'Western Australia' },
    { id: 21, name: 'China', hasChild: true },
    { id: 22, pid: 21, name: 'Guangzhou' },
    { id: 23, pid: 21, name: 'Shanghai' },
    { id: 24, pid: 21, name: 'Beijing' },
    { id: 25, pid: 21, name: 'Shantou' }
];

// Renders treeview
let tree1: TreeView = new TreeView({
    fields: { dataSource: countries, id: 'id', text: 'name', parentID: 'pid', hasChildren: 'hasChild' },
     showCheckBox: true,
     drawNode: drawNode
});
tree1.appendTo('#tree');

// Disables the checkbox alone in treeview
function drawNode(args: DrawNodeEventArgs) {
  let ele: HTMLElement = args.node.querySelector('.e-checkbox-wrapper');
  ele.classList.add('e-checkbox-disabled');
}

```

{% endtab %}