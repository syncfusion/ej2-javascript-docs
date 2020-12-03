# Get all child nodes through parentID

This section demonstrates how to get the child nodes from corresponding parent ID. Using the `getNode` method, you can get the node details of TreeView. Please refer to the following sample.

{% tab template="treeview/how-to/get-child-nodes", sourceFiles="index.ts,index.html,index.css", es5Template="treeview-get-child-nodes-template" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
import { TreeView } from '@syncfusion/ej2-navigations';
enableRipple(true);

/**
 * TreeeView get child nodes from parent id sample
 */

    // List data source for TreeView component
   let data: { [key: string]: Object }[] = [
   {
        code: "AF", name: "Africa", countries: [
            { code: "NGA", name: "Nigeria" },
            { code: "EGY", name: "Egypt" },
            { code: "ZAF", name: "South Africa" }
        ]
    },
    {
        code: "AS", name: "Asia", countries: [
            { code: "CHN", name: "China" },
            { code: "IND", name: "India" , countries: [
              {code: "TN", name: "TamilNadu" }
            ]},
            { code: "JPN", name: "Japan" }
        ]
    },
    {
        code: "EU", name: "Europe", countries: [
            { code: "DNK", name: "Denmark" },
            { code: "FIN", name: "Finland" },
            { code: "AUT", name: "Austria" }
        ]
    },
    {
        code: "NA", name: "North America", countries: [
            { code: "USA", name: "United States of America" },
            { code: "CUB", name: "Cuba" },
            { code: "MEX", name: "Mexico" }
        ]
    },
    {
        code: "SA", name: "South America", countries: [
            { code: "BR", name: "Brazil" },
            { code: "COL", name: "Colombia" },
            { code: "ARG", name: "Argentina" }
        ]
    },
];

let tree1: TreeView = new TreeView({
    fields: { dataSource: data, id: 'code', text: 'name', child: 'countries' },
    loadOnDemand: false,
    created: onCreate
});
tree1.appendTo('#tree');

function onCreate() {
    let proxy = this;
     document.getElementById("btn").addEventListener("click",(event)=>{
          let id = document.getElementById('Nodes').value
          let element= proxy.element.querySelector('[data-uid="' + id + '"]');
          // Gets the child Element
          let liElements = element.querySelectorAll('ul li');
          let arr= [];
              for (let i = 0; i < liElements.length; i++) {
                let nodeData= proxy.getNode(liElements[i]);
                arr.push(nodeData);
                }
                alert(JSON.stringify(arr));
        })
}

```

{% endtab %}