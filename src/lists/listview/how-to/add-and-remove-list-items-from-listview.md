---
title: "ListView how to add and remove list items from listview"
component: "ListView"
description: "ListView how to section, get selected item, dual list, listview filtering, add & remove items from listview, grid layout using listview, listview drag & drop."
---

# How to add and remove list items from listview

You can add or remove list items from the ListView control using the
[`addItem`](../../api/list-view#additem) and
[`removeItem`](../../api/list-view#removeitem) methods.
Refer to the following steps to add or remove a list item.

* Render the ListView with data source, and use the
[template](../../api/list-view#template) property to append the delete icon
for each list item. Also, bind the click event for the delete icon using the
[actionComplete](../../api/list-view#actioncomplete) handler.

* Render the Add Item button, and bind the click event. On the click event handler, pass data with random id to
the [`addItem`](../../api/list-view#additem) method to add a
new list item on clicking the Add Item button.

* Bind the click handler to the delete icon created in step 1. Within the click event, remove the list item by passing the
delete icon list item to
[`removeItem`](../../api/list-view#removeitem) method.

{% tab template="listview/addItem", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css", es5Template="addItem-template" %}

```typescript

import { ListView } from "@syncfusion/ej2-lists";
import { Button } from "@syncfusion/ej2-buttons";
import { MouseEventArgs } from "@syncfusion/ej2-base";

//Define an array of JSON data
let data: { [key: string]: Object }[] = [
    { text: "Hennessey Venom", id: "1", icon: "delete-icon" },
    { text: "Bugatti Chiron", id: "2", icon: "delete-icon" },
    { text: "Bugatti Veyron Super Sport", id: "3", icon: "delete-icon" },
    { text: "Aston Martin One- 77", id: "4", icon: "delete-icon" },
    { text: "Jaguar XJ220", id: "list-5", icon: "delete-icon" },
    { text: "McLaren P1", id: "6", icon: "delete-icon" }
];

//Initialize the ListView control
let listviewInstance: ListView = new ListView({
    //Set the dataSource property
    dataSource: data,
    //Map the appropriate columns to the fields property
    fields: { text: "text", iconCss: "icon" },
    //Set the template for list items
    template: "<div class='text-content'> ${text} <span class = 'delete-icon'></span> </div>",
    //Event handler to bind the click event for delete icon
    actionComplete: onComplete
});
//Render the initialized ListView
listviewInstance.appendTo("#sample-list-flat");

//Initialize the Button control.
let button: Button = new Button();
//Render the initialized button
button.appendTo("#btn");

//Event handler to add the list item on button click
document.getElementById("btn").onclick = () => {
    let data: { [key: string]: Object } = {
        text: "Koenigsegg - " + (Math.random() * 1000).toFixed(0),
        id: (Math.random() * 1000).toFixed(0).toString(),
        icon: "delete-icon"
    };
    listviewInstance.addItem([data]);
    onComplete();
};

//Method for actionComplete handler
function onComplete() {
    let iconEle: HTMLCollection = document.getElementsByClassName("delete-icon");
    //Event handler to bind the click event for delete icon
    Array.prototype.forEach.call(iconEle, (element: HTMLElement) => {
        element.addEventListener("click", deleteItem.bind(this));
    });
}

//Method to delete the list item
function deleteItem(args: MouseEventArgs) {
    args.stopPropagation();
    let liItem: HTMLElement = (args.target as HTMLElement).parentElement.parentElement;
    listviewInstance.removeItem(liItem);
    onComplete();
}

```

{% endtab %}
