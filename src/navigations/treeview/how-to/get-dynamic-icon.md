# Get iconCss dynamically in TreeView

In TreeView component, you can get the original bound data using the `getTreeData` method. For this method, if you pass the id of the tree node, it returns the corresponding node information, or otherwise the overall tree nodes information will be returned. You can use this method to get the bound iconCss class in the `nodeChecking` event. Please refer to the following sample.

{% tab template="treeview/how-to/icon-css", sourceFiles="index.ts,index.html,index.css", es5Template="treeview-dynamic-icon-css-template" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
import { TreeView } from '@syncfusion/ej2-navigations';
enableRipple(true);

/**
 * TreeView dynamic iconCss sample
 */

    // List data source for TreeView component
   let treeData: { [key: string]: Object }[] = [
    {
    "nodeId": "01", "nodeText": "Music", "icon": "folder", "expanded": true,
    "nodeChild": [
      { "nodeId": "01-01", "nodeText": "Gouttes.mp3", "icon": "audio" }
    ]
  },
  {
    "nodeId": "02", "nodeText": "Videos", "icon": "folder", "expanded": true,
    "nodeChild": [
      { "nodeId": "02-01", "nodeText": "Naturals.mp4", "icon": "video" },
      { "nodeId": "02-02", "nodeText": "Wild.mpeg", "icon": "video" }
    ]
  }
];

let tree1: TreeView = new TreeView({
     fields: { dataSource: treeData, id: 'nodeId', text: 'nodeText', child: 'nodeChild', iconCss: 'icon', expanded: 'expanded' },
     showCheckBox: true,
     nodeChecking: onNodeChecking,
     autoCheck: false
});
tree1.appendTo('#tree');

function onNodeChecking(args) {
  let nodeId = args.data[0].id;
  // To get the iconCss
  let iconClass = this.getTreeData(nodeId)[0].icon;
  alert('Icon class is ' + iconClass);
}

```

{% endtab %}