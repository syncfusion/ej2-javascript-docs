# Filter nodes in TreeView

You can filter the tree nodes based on their text using the  `DataManager` plugin and the `fields` property of the TreeView.

The following code example demonstrates how to filter the tree nodes in a TreeView.

{% tab template="treeview/how-to/filtering", sourceFiles="index.ts,index.html,index.css", es5Template="treeview-filtering-template" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
import { TreeView } from '@syncfusion/ej2-navigations';
import { MaskedTextBox } from '@syncfusion/ej2-inputs';
import { DataManager, Query, Predicate } from '@syncfusion/ej2-data';
enableRipple(true);

    // local data source for TreeView component
    let localData: { [key: string]: Object }[] = [
        { id: 1, name: "Australia", hasChild: true },
        { id: 2, pid: 1, name: "New South Wales" },
        { id: 3, pid: 1, name: "Victoria" },
        { id: 4, pid: 1, name: "South Australia" },
        { id: 6, pid: 1, name: "Western Australia" },
        { id: 7, name: "Brazil", hasChild: true },
        { id: 8, pid: 7, name: "Paraná" },
        { id: 9, pid: 7, name: "Ceará" },
        { id: 10, pid: 7, name: "Acre" },
        { id: 11, name: "China", hasChild: true },
        { id: 12, pid: 11, name: "Guangzhou" },
        { id: 13, pid: 11, name: "Shanghai" },
        { id: 14, pid: 11, name: "Beijing" },
        { id: 15, pid: 11, name: "Shantou" },
        { id: 16, name: "France", hasChild: true },
        { id: 17, pid: 16, name: "Pays de la Loire" },
        { id: 18, pid: 16, name: "Aquitaine" },
        { id: 19, pid: 16, name: "Brittany" },
        { id: 20, pid: 16, name: "Lorraine" },
        { id: 21, name: "India", hasChild: true },
        { id: 22, pid: 21, name: "Assam" },
        { id: 23, pid: 21, name: "Bihar" },
        { id: 24, pid: 21, name: "Tamil Nadu" },
        { id: 25, pid: 21, name: "Punjab" }
    ];

    // Render the TreeView with image icons
    let listTreeObj: TreeView = new TreeView({
        fields: { dataSource: localData, id: 'id', parentID: 'pid', text: 'name', hasChildren: 'hasChild' },
    });
    listTreeObj.appendTo('#treeView');

    let mask: MaskedTextBox = new MaskedTextBox({
        placeholder: "Enter the tree node to search",
        change: searchNodes
    });
    mask.appendTo('#mask');

    //Change the dataSource for TreeView
    function changeDataSource(data) {
        listTreeObj.fields = {
            dataSource: data, id: 'id', text: 'name',
            parentID: 'pid', hasChildren: 'hasChild'
        }
    }

    //Filtering the TreeNodes
    function searchNodes(args) {
        let _text = mask.element.value;
        let predicats = [], _array = [], _filter = [];
        if (_text == "") {
            changeDataSource(localData);
        }
        else {
            let predicate = new Predicate('name', 'contains', _text, true);
            let filteredList = new DataManager(localData).executeLocal(new Query().where(predicate));
            for (let j = 0; j < filteredList.length; j++) {
                _filter.push(filteredList[j]["id"]);
                let filters = getFilterItems(filteredList[j], localData);
                for (let i = 0; i < filters.length; i++) {
                    if (_array.indexOf(filters[i]) == -1 && filters[i] != null) {
                        _array.push(filters[i]);
                        predicats.push(new Predicate('id', 'equal', filters[i], false));
                    }
                }
            }
            if (predicats.length == 0) {
                changeDataSource([]);
            } else {
                let query = new Query().where(new Predicate.or(predicats));
                let newList = new DataManager(localData).executeLocal(query);
                changeDataSource(newList);
                setTimeout(function () {
                    listTreeObj.expandAll();
                }, 400);
            }
        }
    }

    //Find the Parent Nodes for corresponding childs
    function getFilterItems(fList, list) {
        let nodes = [];
        nodes.push(fList["id"]);
        let query2 = new Query().where('id', 'equal', fList["pid"], false);
        let fList1 = new DataManager(list).executeLocal(query2);
        if (fList1.length != 0) {
            let pNode = getFilterItems(fList1[0], list);
            for (let i = 0; i < pNode.length; i++) {
                if (nodes.indexOf(pNode[i]) == -1 && pNode[i] != null)
                    nodes.push(pNode[i]);
            }
            return nodes;
        }
        return nodes;
    }
```

{% endtab %}
