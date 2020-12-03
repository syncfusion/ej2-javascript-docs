---
title: "ListView How to drag and drop list items (Reorder) in listview"
component: "ListView"
description: "ListView how to section, get selected item, dual list, listview filtering, add & remove items from listview, grid layout using listview, listview drag & drop."
---

# How to drag and drop list items (Reorder) in listview

In ListView control, we don't have drag and drop support. But we can achieve this requirement using [`TreeView`](https://ej2.syncfusion.com/documentation/treeview/getting-started/) control with ListView appearance.

Drag and Drop in TreeView control was enabled by setting [`allowDragAndDrop`](../../api/treeview#allowdraganddrop) to `true`.

```typescript

let treeViewInstance: TreeView = new TreeView({

    fields: { dataSource: data, id: 'id', text: 'text' },
    allowDragAndDrop: true

});

```

The TreeView control is used to represent hierarchical data in a tree like structure. So, list items in TreeView can be dropped to child of target element. we can prevent this behaviour by cancelling the [`nodeDragStop`](../../api/treeview#nodedragstop) and [`nodeDragging`](../../api/treeview#nodedragging) events.

```typescript

let treeViewInstance: TreeView = new TreeView({
    fields: { dataSource: data, id: 'id', text: 'text' },
    allowDragAndDrop: true,
    nodeDragging: onDragStop,
    nodeDragStop: onDragStop

});

function onDragStop(args: DragAndDropEventArgs) {
    //Block the Child Drop operation in TreeView
   let  draggingItem: HTMLCollection = document.getElementsByClassName("e-drop-in");
    if (draggingItem.length == 1) {
        draggingItem[0].classList.add('e-no-drop');
        args.cancel = true;
    }
}

```

In the below sample, we have rendered draggable list items.

{% tab template="listview/reorder", isDefaultActive = "true", sourceFiles="index.ts,index.html", es5Template="reorder-template"  %}

```typescript

import { TreeView, DragAndDropEventArgs } from '@syncfusion/ej2-navigations';

let data: { [key: string]: Object }[] = [
    { text: 'Hennessey Venom', id: 'list-01' },
    { text: 'Bugatti Chiron', id: 'list-02' },
    { text: 'Bugatti Veyron Super Sport', id: 'list-03' },
    { text: 'SSC Ultimate Aero', id: 'list-04' },
    { text: 'Koenigsegg CCR', id: 'list-05' },
    { text: 'McLaren F1', id: 'list-06' },
    { text: 'Aston Martin One- 77', id: 'list-07' },
    { text: 'Jaguar XJ220', id: 'list-08' },
    { text: 'McLaren P1', id: 'list-09' },
    { text: 'Ferrari LaFerrari', id: 'list-10' },
];
let treeViewInstance: TreeView = new TreeView({
    fields: { dataSource: data, id: 'id', text: 'text' },
    allowDragAndDrop: true,
    nodeDragging: onDragStop,
    nodeDragStop: onDragStop

});

treeViewInstance.appendTo('#element');

function onDragStop(args: DragAndDropEventArgs) {
    //Block the Child Drop operation in TreeView
   let  draggingItem: HTMLCollection = document.getElementsByClassName("e-drop-in");
    if (draggingItem.length == 1) {
        draggingItem[0].classList.add('e-no-drop');
        args.cancel = true;
    }
}

```

{% endtab %}
