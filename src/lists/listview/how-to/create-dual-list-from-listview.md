---
title: "ListView how To create dual list from listview"
component: "ListView"
description: "ListView how to section, get selected item, dual list, listview filtering, add & remove items from listview, grid layout using listview, listview drag & drop."
---

# How to create dual list from listview

The dual list contains two ListView. This allows you to move list items from one list to another using the client-side
events. This section explains how to integrate the ListView control to achieve dual list.

## Use cases

* Stock exchanges of two different countries
* Job applications (skill sets)

## Integration of Dual List

Here, two ListView controls have been used to display the list items. An ej2-button is used to transfer data between
the ListView, and a textbox is used to achieve the UI of filtering support.

The dual list supports:

* Moving whole data from one list to another.
* Moving selected data from one list to another.
* Filtering the list by using a client-side typed character.

In the ListView control, sorting is enabled using the
[sortOrder](../../api/list-view/#sortorder) property, and
the [select](../../api/list-view#select) event is triggered
while selecting an item. Here, the select event is triggered to enable and disable button states.

## Manipulating data

## Moving whole data from the first list to the second list(>>)

Here, the whole data can be moved from the first ListView to the second by clicking the first button. When clicking the button,
the whole list items are sliced, and `concat` with the second ListView. This button is enabled only when the data source
of the first ListView is not empty.

## Moving whole data from the second list to the first list(<<)**

The functionality of the second button is the same as above, and data is transferred from the second list to the first
list. This button is enabled only when the data source of the second ListView is not empty.

## Moving selected item from one list to another list (>) and (<)**

The [Select](../../api/list-view#select) event is triggered
when selecting a list item in the ListView. The selected items can be transferred between two lists. These buttons will be
enabled when selecting an item in lists.

## Filtering method

The filtering method is used to filter list items when typing a character in the text box. In this
method, the [`dataManager`](../../data/getting-started/) has been
used to fetch data from the data source and display in ListView.

## Sorting

By using the dual list, list items can be sorted in the ListView control using the
[sortOrder](../../api/list-view#sortorder) property.
You can enable sorting in one ListView; in the same order, data can be transferred to another ListView.

{% tab template="listview/dual-list", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css", es5Template="dual-template" %}

```typescript

import { ListView, SelectedItem } from '@syncfusion/ej2-lists';
import { Button } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';
import { DataManager, Query } from '@syncfusion/ej2-data';
enableRipple(true);
//Define an array of JSON data
let firstListData: { [key: string]: Object }[] = [
    { text: 'Hennessey Venom', id: 'list-01' },
    { text: 'Bugatti Chiron', id: 'list-02' },
    { text: 'Bugatti Veyron Super Sport', id: 'list-03' },
    { text: 'SSC Ultimate Aero', id: 'list-04' },
    { text: 'Koenigsegg CCR', id: 'list-05' },
    { text: 'McLaren F1', id: 'list-06' },

];

let secondListData: { [key: string]: Object }[] = [
    { text: 'Aston Martin One- 77', id: 'list-07' },
    { text: 'Jaguar XJ220', id: 'list-08' },
    { text: 'McLaren P1', id: 'list-09' },
    { text: 'Ferrari LaFerrari', id: 'list-10' },
];


// Initialize the ListView control
let listObj1: ListView = new ListView({

    //Set the defined data to the dataSource property
    dataSource: firstListData.slice(),

    //Map the appropriate columns to the fields property
    fields: { text: 'text', id: 'id' },
    sortOrder: 'Ascending',
    select: onFirstListSelect

});

//Render the initialized ListView control
listObj1.appendTo('#list-1');

let listObj2: ListView = new ListView({

    //Set the defined data to the dataSource property
    dataSource: secondListData.slice(),

    //Map the appropriate columns to the fields property
    fields: { text: 'text', id: 'id' },
    sortOrder: 'Ascending',
    select: onSeconListSelect

});

//Render the initialized ListView control
listObj2.appendTo('#list-2');

let btnobj1: Button = new Button();
btnobj1.appendTo('#firstBtn');
let btnobj2: Button = new Button({
    disabled: true
});
btnobj2.appendTo('#secondBtn');
let btnobj3: Button = new Button({
    disabled: true
});
btnobj3.appendTo('#thirdBtn');
let btnobj4: Button = new Button();
btnobj4.appendTo('#fourthBtn');


//Here, all list items are moved to the second list on clicking move all button
btnobj1.element.addEventListener('click', () => {
    listObj2.dataSource = Array.prototype.concat.call(listObj1.dataSource, listObj2.dataSource);
    listObj2.dataBind();
    updateFirstListData();
    listObj1.removeMultipleItems(Array.prototype.slice.call(listObj1.element.querySelectorAll('.e-list-item')));
    firstListData = firstListData.concat(listObj1.dataSource as { [key: string]: Object }[]);
    secondListData = (listObj2.dataSource as { [key: string]: Object }[]).slice();
    btnobj1.disabled = true;
    onFirstKeyUp();
    setButtonState();
});

//Here, the selected list items are moved to the second list on clicking move button
btnobj2.element.addEventListener('click', () => {
    let selectedItem: SelectedItem = listObj1.getSelectedItems() as SelectedItem;
    listObj2.dataSource = Array.prototype.concat.call(listObj2.dataSource, selectedItem.data);
    listObj2.dataBind();
    updateFirstListData();
    listObj1.removeItem(selectedItem.item);
    firstListData = firstListData.concat(listObj1.dataSource as { [key: string]: Object }[]);
    secondListData = (listObj2.dataSource as { [key: string]: Object }[]).slice();
    onFirstKeyUp();
    btnobj2.disabled = true;
    setButtonState();
});

//Here, the selected list items are moved to the first list on clicking move button
btnobj3.element.addEventListener('click', () => {
    let selectedItem: SelectedItem = listObj2.getSelectedItems() as SelectedItem;
    listObj1.dataSource = Array.prototype.concat.call(listObj1.dataSource, selectedItem.data);
    listObj1.dataBind();
    updateSecondListData();
    listObj2.removeItem(selectedItem.item);
    secondListData = secondListData.concat(listObj2.dataSource as { [key: string]: Object }[]);
    firstListData = (listObj1.dataSource as { [key: string]: Object }[]).slice();
    onSecondKeyUp();
    btnobj3.disabled = true;
    setButtonState();

});

//Here, all list items are moved to the first list on clicking move all button
btnobj4.element.addEventListener('click', () => {
    listObj1.dataSource = Array.prototype.concat.call(listObj1.dataSource, listObj2.dataSource);
    listObj1.dataBind();
    updateSecondListData();
    listObj2.removeMultipleItems(Array.prototype.slice.call(listObj2.element.querySelectorAll('.e-list-item')));
    secondListData = secondListData.concat(listObj2.dataSource as { [key: string]: Object }[]);
    firstListData = (listObj1.dataSource as { [key: string]: Object }[]).slice();
    onSecondKeyUp();
    setButtonState();

});

//Here, the ListView data source is updated to the first list
function updateFirstListData() {
    Array.prototype.forEach.call(listObj1.element.querySelectorAll('.e-list-item'), (list: HTMLLIElement) => {
        firstListData.forEach((data, index) => {
            if (list.innerText.trim() === data.text) {
                firstListData.splice(index, 1)
            }
        });
    });
    (document.getElementById("firstInput") as HTMLInputElement).value = '';
    let ds: { [key: string]: Object }[] = [];
    firstListData.forEach((data) => {
        ds.push(data);
    })
    firstListData = ds;

}

//Here, the ListView dataSource is updated for the second list
function updateSecondListData() {
    Array.prototype.forEach.call(listObj2.element.querySelectorAll('.e-list-item'), (list: HTMLLIElement) => {
        secondListData.forEach((data, index) => {
            if (list.innerText.trim() === data.text) {
                secondListData.splice(index, 1)
            }
        });

    });
    (document.getElementById("secondInput") as HTMLInputElement).value = '';
    let ds: { [key: string]: Object }[] = [];
    secondListData.forEach((data) => {
        ds.push(data);
    })
    secondListData = ds;

}
function onFirstListSelect() {
    btnobj2.disabled = false;
}
function onSeconListSelect() {
    btnobj3.disabled = false;
}
document.getElementById('firstInput').addEventListener('keyup', onFirstKeyUp);
//Here, filtering is handled using the dataManager for the first list
function onFirstKeyUp() {
    let value: string = (document.getElementById("firstInput") as HTMLInputElement).value;
    var data: Object[] = new DataManager(firstListData).executeLocal(new Query().where('text', 'startswith', value, true));
    if (!value) {
        listObj1.dataSource = firstListData.slice();
    } else {
        listObj1.dataSource = data as { [key: string]: Object }[];
    }
    listObj1.dataBind();

}
document.getElementById('secondInput').addEventListener('keyup', onSecondKeyUp);
//Here, filtering is handled using the dataManager for the second list
function onSecondKeyUp() {
    let value: string = (document.getElementById("secondInput") as HTMLInputElement).value;
    var data: Object[] = new DataManager(secondListData).executeLocal(new Query().where('text', 'startswith', value, true));
    if (!value) {
        listObj2.dataSource = secondListData.slice();
    } else {
        listObj2.dataSource = data as { [key: string]: Object }[];
    }
    listObj2.dataBind();
}

//Here, the state of the button is changed
function setButtonState() {
    if ((listObj1.dataSource as { [key: string]: Object }[]).length) {
        btnobj1.disabled = false;
    } else {
        btnobj1.disabled = true;
        btnobj2.disabled = true;
    }

    if ((listObj2.dataSource as { [key: string]: Object }[]).length) {
        btnobj4.disabled = false;
    } else {
        btnobj4.disabled = true;
        btnobj3.disabled = true;
    }

}

```

{% endtab %}
