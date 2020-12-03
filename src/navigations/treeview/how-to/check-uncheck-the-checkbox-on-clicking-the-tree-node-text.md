# Check/uncheck the checkbox on clicking the tree node text

You can check and uncheck the checkboxes of tree view by clicking the tree node using the `nodeClicked` event of TreeView.

{% tab template="treeview/how-to/check-text-node", sourceFiles="index.ts,index.html,index.css", es5Template="treeview-check-text-node-template" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
import { TreeView } from '@syncfusion/ej2-navigations';
enableRipple(true);

/**
 * TreeView check/uncheck the check box, while clicking on the tree node text sample
 */

    // Data source for TreeView component
    let countries: { [key: string]: Object } [] = [
    { id: 1, name: 'Australia', hasChild: true, expanded: true },
    { id: 2, pid: 1, name: 'New South Wales' },
    { id: 3, pid: 1, name: 'Victoria' },
    { id: 4, pid: 1, name: 'South Australia' },
    { id: 6, pid: 1, name: 'Western Australia' },
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

    // Render the TreeView with checkboxes
    let treeObj: TreeView = new TreeView({
    fields: { dataSource: countries, id: 'id', parentID: 'pid', text: 'name', hasChildren: 'hasChild' },
    showCheckBox: true,
    nodeClicked: nodeCheck,
    keyPress: nodeCheck
});
treeObj.appendTo('#tree');

function nodeCheck(args: NodeKeyPressEventArgs | NodeClickEventArgs ): void {
    let checkedNode: any = [args.node];
    if (args.event.target.classList.contains('e-fullrow') || args.event.key == "Enter") {
       let getNodeDetails: any = treeObj.getNode(args.node);
        if (getNodeDetails.isChecked == 'true') {
            treeObj.uncheckAll(checkedNode);
        } else {
            treeObj.checkAll(checkedNode);
        }
    }
}


```

{% endtab %}
