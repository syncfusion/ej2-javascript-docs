---
title: "ListView how to customize listview as grid layout"
component: "ListView"
description: "ListView how to section, get selected item, dual list, listview filtering, add & remove items from listview, grid layout using listview, listview drag & drop."
---

# How to customize listview as grid layout

In Listview, list items can be rendered in grid layout with following data manipulations.

* Add Item

* Remove Item

* Sort Items

* Filter Items

## Grid Layout

In this section, we will discuss about rendering of list items in grid layout.

* Initialize and render ListView with dataSource which will render list items in list layout.

* Now, add the below CSS to list item. This will make list items to render in grid layout

```css

#default-list .e-list-item {
        height: 100px;
        width: 100px;
        float: left;
}

```

In the below sample, we have rendered List items in grid layout.

{% tab template="listview/grid-layout", isDefaultActive = "true", sourceFiles="index.ts,index.html", es5Template="grid-layout-template"  %}

```typescript

import { ListView } from '@syncfusion/ej2-lists';

//define the array of string
let data: number[] = [1, 2, 3, 4, 5, 6, 7, 8, 9];

//Initialize ListView control
let listViewInstance: ListView = new ListView({
    //set the data to datasource property
    dataSource: data,
    //set the template for list items
    template: '<img id="listImage" src="./apple.png" alt="apple" />'
});

//Render initialized ListView
listViewInstance.appendTo("#element");

```

{% endtab %}

## Data manipulation

In this section, we will discuss about ListView data manipulations.

### Add Item

We can add list item using [`addItem`](../../api/list-view#additem) API. This will accept array of data as argument.

```typescript

 listViewInstance.addItem([{text: 'Apricot', id: '32'}]);

```

In the below sample, you can add new fruit item by clicking add button which will open dialog box with fruit name and image URL text box. After entering the item details, click the add button. This will add your new fruit item.

### Remove item

We can remove list item using [`removeItem`](../../api/list-view#removeitem) API. This will accept fields with `id` or list item element as argument.

```typescript

 listViewInstance.removeItem({id: '32'});

```

In the below sample, you can remove fruit by hovering the fruit item which will show delete button and click that delete button to delete that fruit from your list.

### Sort Items

Listview can be sorted either in Ascending or Descending order. To enable sorting in your ListView, set [`sortOrder`](../../api/list-view#sortorder) as `Ascending` or `Descending`.

```typescript

let listViewInstance: ListView = new ListView({
    sortOrder: 'Ascending';
})

```

We can also set sorting after control initialization.

```typescript

listViewInstance.sortOrder = 'Ascending'

```

In the below sample, we have sorted fruits in `Ascending` order. To sort it in descending, click on sort order icon and vice versa.

### Filter Items

Listview data can be filtered with the help of [`dataManager`](../../data/getting-started/). After filtering the data, update ListView [`dataSource`](../../api/list-view#datasource) with filtered data.

```typescript

let value = document.getElementById("filter").value;  //input text box value
let filteredData = new DataManager(listdata).executeLocal(
        new Query().where("text", "startswith", value, true)
);

listViewInstance.dataSource = filteredData;

```

In the below sample, we can filter fruit items with the help of search text box. This will filter fruit items based on your input. Here we used [`startswith`](../../data/querying#filter-operators) of input text to filter data in DataManager.

{% tab template="listview/manipulation", isDefaultActive = "true", sourceFiles="index.ts,index.html,index.css", es5Template="manipulation-template"  %}

```typescript

import { ListView, SelectedItem } from '@syncfusion/ej2-lists';
import { Dialog } from '@syncfusion/ej2-popups';
import { closest, enableRipple, MouseEventArgs } from '@syncfusion/ej2-base';
import { DataManager, Query } from "@syncfusion/ej2-data";
enableRipple(true);

let ascClass = 'e-sort-icon-ascending';
let desClass = 'e-sort-icon-descending';

//define the array of JSON
let fruitsdata: { [key: string]: Object }[] = [
    { text: 'Date', id: '1', imgUrl: './dates.jpg' },
    { text: 'Fig', id: '2', imgUrl: './fig.jpg' },
    { text: 'Apple', id: '3', imgUrl: './apple.png' },
    { text: 'Apricot', id: '4', imgUrl: './apricot.jpg' },
    { text: 'Grape', id: '5', imgUrl: './grape.jpg' },
    { text: 'Strawberry', id: '6', imgUrl: './strawberry.jpg' },
    { text: 'Pineapple', id: '7', imgUrl: './pineapple.jpg' },
    { text: 'Melon', id: '8', imgUrl: './melon.jpg' },
    { text: 'Lemon', id: '9', imgUrl: './lemon.jpg' },
    { text: 'Cherry', id: '10', imgUrl: './cherry.jpg' },
];

//Initialize ListView control
let listViewInstance: ListView = new ListView({

    //set the data to datasource property
    dataSource: fruitsdata.slice(),

    //set the template for list items
    template: '<div class="fruits"><div class="first"><img id="listImage" src="${imgUrl}" alt="fruit" /><button class="delete e-control e-btn e-small e-round e-delete-btn e-primary e-icon-btn" data-ripple="true"><span class="e-btn-icon e-icons delete-icon"></span></button></div><div class="fruitName">${text}</div></div>',

    //set sortOrder for list items
    sortOrder: 'Ascending',
    actionComplete: () => {
        wireEvents();
    }

});

//Render initialized ListView
listViewInstance.appendTo('#element');

let dialogObj: Dialog = new Dialog({
    header: 'Add fruit',
    content: '<div id="listDialog"><div class="input_name"><label for="name">Fruit Name: </label><input id="name" class="e-input" type="text" placeholder="Enter fruit name"/></div><div><label for="imgurl">Fruit Image: </label><input id="imgurl" class="e-input" type="text" placeholder="Enter image url"/></div></div>',
    showCloseIcon: true,
    buttons: [{
        click: dlgButtonClick,
        buttonModel: { content: 'Add', isPrimary: true }
    }],
    width: '300px',
    visible: false
});

dialogObj.appendTo('#dialog');

function addItem() {
    (document.getElementById("name") as HTMLInputElement).value = "";
    (document.getElementById("imgurl") as HTMLInputElement).value = "";
    dialogObj.show()
}

function wireEvents() {
    Array.prototype.forEach.call(document.getElementsByClassName('e-delete-btn'), (ele: HTMLButtonElement) => {
        ele.addEventListener('click', onDeleteBtnClick);
    });
    document.getElementById("add").addEventListener('click', addItem);
    document.getElementById("sort").addEventListener('click', sortItems);
    document.getElementById("search").addEventListener("keyup", onKeyUp);
}

//Here we are removing list item
function onDeleteBtnClick(e: MouseEventArgs) {
    e.stopPropagation();
    let li: Element = closest(e.currentTarget as Element, '.e-list-item');
    let data = listViewInstance.findItem(li);
    listViewInstance.removeItem(data as any);
    new DataManager(fruitsdata).remove('id', { id: (<{ [key: string]: any }>data)["id"] });
}

//Here we are adding list item
function dlgButtonClick() {
    let name: string = (document.getElementById("name") as HTMLInputElement).value;
    let url: string = (document.getElementById("imgurl") as HTMLInputElement).value;
    let id: number = Math.random() * 10000;
    listViewInstance.addItem([{ text: name, id: id, imgUrl: url }]);
    fruitsdata.push({ text: name, id: id, imgUrl: url });
    listViewInstance.element.querySelector('[data-uid="' + id + '"]').getElementsByClassName('e-delete-btn')[0].addEventListener('click', onDeleteBtnClick);
    dialogObj.hide();
}

//Here we are sorting list item
function sortItems() {
    let ele: Element = document.getElementById("sort").firstElementChild;
    let des = ele.classList.contains(desClass) ? true : false;
    if (des) {
        ele.classList.remove(desClass);
        ele.classList.add(ascClass);
        listViewInstance.sortOrder = 'Ascending'
    } else {
        ele.classList.remove(ascClass);
        ele.classList.add(desClass);
        listViewInstance.sortOrder = 'Descending'
    }
    listViewInstance.dataBind();
    wireEvents();
}

//Here, the list items are filtered using the DataManager instance.
function onKeyUp() {
    let value: string = (document.getElementById("search") as HTMLInputElement).value;
    let data: Object[] = new DataManager(fruitsdata).executeLocal(
        new Query().where("text", "startswith", value, true)
    );
    if (!value) {
        listViewInstance.dataSource = fruitsdata.slice();
    } else {
        listViewInstance.dataSource = data as { [key: string]: Object }[];
        listViewInstance.dataBind();
    }
}

```

{% endtab %}
