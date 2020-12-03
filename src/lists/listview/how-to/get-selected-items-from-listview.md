---
title: "How to get selected items from listview"
component: "ListView"
description: "ListView how to section, get selected item, dual list, listview filtering, add & remove items from listview, grid layout using listview, listview drag & drop."
---

# How to get selected items from listview

Single or many items can be selected by users in the ListView control. An API is used to get selected items from the
list items. This is called as the
[`getSelectedItems`](../../api/list-view#getselecteditems)
method.

**`getSelectedItems` method**

This is used to get the details of the currently selected item from the list items. It returns the
[`SelectedItem`](../../api/list-view/selectedItem/) |
[`SelectedCollection`](../../api/list-view/selectedCollection/)

The `getSelectedItems` method returns the following items from the selected list items.

| Return type | Purpose |
|------------|-------------------|
| text | Returns the text of selected item lists |
| data | Returns the whole data of selected list items, i.e., returns the fields data of selected li.|
| item | Returns the collections of list items |

{% tab template="listview/selected-item", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css", es5Template="selected-item" %}

```typescript

import { ListView, SelectedCollection } from '@syncfusion/ej2-lists';
import { Button } from '@syncfusion/ej2-buttons';
//define the array of string
let data: { [key: string]: Object }[] = [
    { text: 'Hennessey Venom', id: 'list-01' },
    { text: 'Bugatti Chiron', id: 'list-02', isChecked: true },
    { text: 'Bugatti Veyron Super Sport', id: 'list-03' },
    { text: 'SSC Ultimate Aero', id: 'list-04', isChecked: true },
    { text: 'Koenigsegg CCR', id: 'list-05' },
    { text: 'McLaren F1', id: 'list-06' },
    { text: 'Aston Martin One- 77', id: 'list-07', isChecked: true },
    { text: 'Jaguar XJ220', id: 'list-08' }
];

//Initialize the ListView control
let listviewInstance: ListView = new ListView({
    //set the data to the dataSource property
    dataSource: data,

    //Enable check box
    showCheckBox: true,
});

//Render the initialized ListView
listviewInstance.appendTo("#element");

let button: Button = new Button();
button.appendTo("#btn")

document.getElementById('btn').addEventListener('click', () => {
    let selecteditem: SelectedCollection = listviewInstance.getSelectedItems() as SelectedCollection;
    let data: HTMLElement = document.getElementById('val');
    data.innerHTML = "";
    let row1: HTMLTableRowElement = document.createElement('tr');
    let header1: HTMLTableHeaderCellElement = document.createElement('th');
    header1.innerHTML = 'Text';
    row1.appendChild(header1);
    let header2 = document.createElement('th');
    header2.innerHTML = 'Id';
    row1.appendChild(header2);
    document.getElementById('val').appendChild(row1);
    for (let i: number = 0; i < (selecteditem["data"] as { [key: string]: object }[]).length; i++) {
        let row2: HTMLTableRowElement = document.createElement('tr');
        row2.setAttribute("id", i.toString());
        let data1: HTMLElement = document.createElement('td');
        data1.innerHTML = selecteditem["text"][i];
        row2.appendChild(data1);
        let data2: HTMLElement = document.createElement('td');
        data2.innerHTML = (selecteditem["data"] as { [key: string]: object }[])[i].id.toString();
        row2.appendChild(data2);
        document.getElementById('val').appendChild(row2);
    }

});

```

{% endtab %}
