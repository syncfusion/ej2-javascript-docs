# Select one child at a time out of one specific parent

TreeView allows both single and multiple selections. If your application needs to select one child at a time under one specific parent, refer to the following example. Here, you can achieve this in the `nodeSelecting` event of TreeView. However, you can reset the selected child and make another selection by pressing Ctrl + selected nodes.

{% tab template="treeview/how-to/select-one-child", sourceFiles="index.ts,index.html,index.css", es5Template="treeview-select-one-child-template" %}

```typescript

import { TreeView } from '@syncfusion/ej2-navigations';

/**
 * Single child selection at a time
 */

    // List data source for TreeView component
   let localData: { [key: string]: Object }[] = [
    { id: 1, name: 'Parent 1', hasChild: true, expanded: true },
    { id: 2, pid: 1, name: 'Child 1' },
    { id: 3, pid: 1, name: 'Child 2' },
    { id: 4, pid: 1, name: 'Child 3' },
    { id: 7, name: 'Parent 2', hasChild: true, expanded: true },
    { id: 8, pid: 7, name: 'Child 1' },
    { id: 9, pid: 7, name: 'Child 2' },
    { id: 10, pid: 7, name: 'Child 3' },
];

let tree1: TreeView = new TreeView({
    fields: { dataSource: localData, id: 'id', text: 'name', parentID: 'pid', hasChildren: 'hasChild' },
    loadOnDemand: false,
    allowMultiSelection: true
    nodeSelecting: onNodeSelecting
});
tree1.appendTo('#tree');

  let parent,child;
  let count: boolean = false;
  let childCount: boolean = false;

  function onNodeSelecting(args: NodeSelectEventArgs) {
    let id = args.nodeData.parentID;
    if (!count) {
       parent = id;
       count = true;
    }
    if (!childCount){
       child = args.nodeData.id;
       childCount = true
    }
    if (id != null && id === parent) {
      let element: HTMLElement = tree1.element.querySelector('[data-uid="' + id + '"]');
      let liElements = element.querySelectorAll('ul li');
      for (let i: number = 0; i < liElements.length; i++) {
        let nodeData = tree1.getNode(liElements[i]);
        if (nodeData.selected && args.action === "select" && child !== args.nodeData.id) {
          args.cancel = true;
        }
        // For unselect the selectedNodes
        else  if (args.action === "un-select" && child === args.nodeData.id) {
          childCount = false;
          child = null;
          parent = null;
          count = false;
        }
      }
    } else if (id !== parent && id !== null) {
        if(args.action == "select"){
          args.cancel = true
        }
    } else if (id === null){
       childCount = false;
         child = null;
          parent = null;
          count = false
    }
}

```

{% endtab %}