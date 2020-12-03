# Validate the text when renaming the tree node

You can validate the tree node text while editing using `nodeEdited` event of the TreeView. Following is an example that shows how to validate and prevent empty values in tree node.

{% tab template="treeview/how-to/validation", sourceFiles="index.ts,index.html,index.css", es5Template="treeview-validation-template" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
import { TreeView } from '@syncfusion/ej2-navigations';
enableRipple(true);

/**
 * TreeView node editing sample with validation
 */

    // Hierarchical data source for TreeView component
    let treeData: { [key: string]: Object } [] = [
    {
        id: 1, name: 'Discover Music', expanded: true,
        child: [
            { id: 2, name: 'Hot Singles' },
            { id: 3, name: 'Rising Artists' },
            { id: 4, name: 'Live Music' }
        ]
    },
    {
        id: 7, name: 'Sales and Events',
        child: [
            { id: 8, name: '100 Albums - $5 Each' },
            { id: 9, name: 'Hip-Hop and R&B Sale' },
            { id: 10, name: 'CD Deals' }
        ]
    },
    {
        id: 11, name: 'Categories',
        child: [
            { id: 12, name: 'Songs' },
            { id: 13, name: 'Bestselling Albums' },
            { id: 14, name: 'New Releases' },
            { id: 15, name: 'Bestselling Songs' }
        ]
    },
    {
        id: 16, name: 'MP3 Albums',
        child: [
            { id: 17, name: 'Rock' },
            { id: 18, name: 'Gospel' },
            { id: 19, name: 'Latin Music' },
            { id: 20, name: 'Jazz' }
        ]
    },
    {
        id: 21, name: 'More in Music',
        child: [
            { id: 22, name: 'Music Trade-In' },
            { id: 23, name: 'Redeem a Gift Card' },
            { id: 24, name: 'Band T-Shirts' }
        ]
    }
];

    // Render the TreeView with editing option
    let treeObj: TreeView = new TreeView({
    fields: { dataSource: treeData, id: 'id', text: 'name', child: 'child' },
    allowEditing: true,
    nodeEdited: onNodeEdited
});
treeObj.appendTo('#tree');

function onNodeEdited(args: NodeEditEventArgs): void {
    let displayContent:string = "";
    if (args.newText.trim() == "") {
        args.cancel=true;
        displayContent = "TreeView item text should not be empty";
    }
    else if (args.newText != args.oldText) {
        displayContent = "TreeView item text edited successfully";
    } else {
        displayContent = "";
    }
    document.getElementById("display").innerHTML = displayContent;
}


```

{% endtab %}