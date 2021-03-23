---
title: "Drag and Drop"
component: "Tab"
description: "Drag and drop functionality in tab"
---

# Drag and drop items

The Tab component allows you to drag and drop any item by setting [allowDragAndDrop](../api/tab#allowdraganddrop)&nbsp;to **true**. Items can be reordered to any place by dragging and dropping them onto the desired location.

* If you need to prevent dragging action for a particular item, the [`onDragStart`](../api/tab#ondragstart) event can be used which will trigger when the item drag is started. If you need to prevent dropping action for a particular item, the [`dragged`](../api/tab#dragged) event can be used which will trigger when the drag action is stopped.

* The [`dragArea`](../api/tab#dragArea) defines the area in which the draggable element movement will be occurring. Outside that area will be restricted for the draggable element movement.

* The [`onDragStart`](../api/tab#ondragstart) event will be triggered before dragging the item from Tab.

* The [`dragging`](../api/tab#dragging) event will be triggered when the Tab item is being dragged.

* The [`dragged`](../api/tab#dragged) event will be triggered when the Tab item is dropped on the target element successfully.

In the following sample, the [allowDragAndDrop](../api/tab#allowdraganddrop) property is enabled.

{% tab template="tab/drag-and-drop/default", sourceFiles="index.ts,index.html", es5Template="tab-default-template" %}

```typescript

import { Tab } from '@syncfusion/ej2-navigations';

let tabObj: Tab = new Tab({
    heightAdjustMode: 'Auto',
    allowDragAndDrop: true,
    dragArea: '#container',
    items: [
        {
            header: { text: 'India' },
            content: 'India officially the Republic of India, is a country in South Asia. It is the seventh-largest country by area, the second-most populous country with over 1.2 billion people, and the most populous democracy in the world. Bounded by the Indian Ocean on the south, the Arabian Sea on the south-west, and the Bay of Bengal on the south-east, it shares land borders with Pakistan to the west;China, Nepal, and Bhutan to the north-east; and Burma and Bangladesh to the east. In the Indian Ocean, India is in the vicinity of Sri Lanka and the Maldives; in addition, India Andaman and Nicobar Islands share a maritime border with Thailand and Indonesia.'
        },
        {
            header: { text: 'Australia' },
            content: 'Australia, officially the Commonwealth of Australia, is a country comprising the mainland of the Australian continent, the island of Tasmania and numerous smaller islands. It is the world sixth-largest country by total area. Neighboring countries include Indonesia, East Timor and Papua New Guinea to the north; the Solomon Islands, Vanuatu and New Caledonia to the north-east; and New Zealand to the south-east.'
        },
        {
            header: { text: 'USA' },
            content: 'The United States of America (USA or U.S.A.), commonly called the United States (US or U.S.) and America, is a federal republic consisting of fifty states and a federal district. The 48 contiguous states and the federal district of Washington, D.C. are in central North America between Canada and Mexico. The state of Alaska is west of Canada and east of Russia across the Bering Strait, and the state of Hawaii is in the mid-North Pacific. The country also has five populated and nine unpopulated territories in the Pacific and the Caribbean.'
        },
        {
            header: { text: 'France' },
            content: 'France, officially the French Republic is a sovereign state comprising territory in western Europe and several overseas regions and territories. The European part of France, called Metropolitan France, extends from the Mediterranean Sea to the English Channel and the North Sea, and from the Rhine to the Atlantic Ocean; France covers 640,679 square kilo metres and as of August 2015 has a population of 67 million, counting all the overseas departments and territories.'
        }
    ],
});
tabObj.appendTo('#draggableTab');

```

{% endtab %}

## Drag and drop item between tabs

It is possible to drag and drop the tab items between two tabs, by manually saving those dropped items as new tab item data through the `addTab` method of Tab and removing the dragged item through the `removeTab` method of Tab.

In this example, we have used the tab control as an external source, and the item from the tab component is dragged and dropped onto another Tab. Therefore, it is necessary to use the `onDragStart` and `dragged` event of the Tab component, where we can form an event object and save it using the `addTab` method of the Tab and remove the dragged item through `removeTab` method of Tab using the dragged item index.

{% tab template="tab/drag-and-drop/tab-to-tab", sourceFiles="index.ts,index.html", es5Template="tab-to-tab-template" %}

```typescript

import { isNullOrUndefined } from '@syncfusion/ej2-base';
import { Tab, DragEventArgs } from '@syncfusion/ej2-navigations';

let firstTabObj: Tab = new Tab({
    heightAdjustMode: 'Auto',
    allowDragAndDrop: true,
    dragArea: '#container',
    onDragStart: firstTabdragStart,
    dragged: firstTabDragStop,
    items: [
        {
            header: { text: 'India' },
            content: 'India officially the Republic of India, is a country in South Asia. It is the seventh-largest country by area, the second-most populous country with over 1.2 billion people, and the most populous democracy in the world. Bounded by the Indian Ocean on the south, the Arabian Sea on the south-west, and the Bay of Bengal on the south-east, it shares land borders with Pakistan to the west;China, Nepal, and Bhutan to the north-east; and Burma and Bangladesh to the east. In the Indian Ocean, India is in the vicinity of Sri Lanka and the Maldives; in addition, India Andaman and Nicobar Islands share a maritime border with Thailand and Indonesia.'
        },
        {
            header: { text: 'Australia' },
            content: 'Australia, officially the Commonwealth of Australia, is a country comprising the mainland of the Australian continent, the island of Tasmania and numerous smaller islands. It is the world sixth-largest country by total area. Neighboring countries include Indonesia, East Timor and Papua New Guinea to the north; the Solomon Islands, Vanuatu and New Caledonia to the north-east; and New Zealand to the south-east.'
        },
        {
            header: { text: 'USA' },
            content: 'The United States of America (USA or U.S.A.), commonly called the United States (US or U.S.) and America, is a federal republic consisting of fifty states and a federal district. The 48 contiguous states and the federal district of Washington, D.C. are in central North America between Canada and Mexico. The state of Alaska is west of Canada and east of Russia across the Bering Strait, and the state of Hawaii is in the mid-North Pacific. The country also has five populated and nine unpopulated territories in the Pacific and the Caribbean.'
        },
        {
            header: { text: 'France' },
            content: 'France, officially the French Republic is a sovereign state comprising territory in western Europe and several overseas regions and territories. The European part of France, called Metropolitan France, extends from the Mediterranean Sea to the English Channel and the North Sea, and from the Rhine to the Atlantic Ocean; France covers 640,679 square kilo metres and as of August 2015 has a population of 67 million, counting all the overseas departments and territories.'
        }
    ],

});
firstTabObj.appendTo('#firstTab');

let secondTabObj: Tab = new Tab({
    heightAdjustMode: 'Auto',
    dragArea: '#container',
    allowDragAndDrop: true,
    onDragStart: secondTabDragStart,
    dragged: secondTabDragStop,
    items: [
        {
            header: { text: 'HTML' },
            content: 'HyperText Markup Language, commonly referred to as HTML, is the standard markup language used to create web pages. Along with CSS, and JavaScript, HTML is a cornerstone technology, used by most websites to create visually engaging web pages, user interfaces for web applications, and user interfaces for many mobile applications.[1] Web browsers can read HTML files and render them into visible or audible web pages. HTML describes the structure of a website semantically along with cues for presentation, making it a markup language, rather than a programming language.'
        },
        {
            header: { text: 'C Sharp(C#)' },
            content: 'C# is intended to be a simple, modern, general-purpose, object-oriented programming language. Its development team is led by Anders Hejlsberg. The most recent version is C# 5.0, which was released on August 15, 2012.'
        },
        {
            header: { text: 'Java' },
            content: 'Java is a set of computer software and specifications developed by Sun Microsystems, later acquired by Oracle Corporation, that provides a system for developing application software and deploying it in a cross-platform computing environment. Java is used in a wide variety of computing platforms from embedded devices and mobile phones to enterprise servers and supercomputers. While less common, Java applets run in secure, sandboxed environments to provide many features of native applications and can be embedded in HTML pages.'
        },
        {
            header: { text: 'VB.Net' },
            content: 'The command-line compiler, VBC.EXE, is installed as part of the freeware .NET Framework SDK. Mono also includes a command-line VB.NET compiler. The most recent version is VB 2012, which was released on August 15, 2012.'
        }
    ],

});
secondTabObj.appendTo('#secondTab');

let firstTabitem: object[];
let secondTabitem: object[];
let dragItemIndex: number;
let dragItemContainer: HTMLElement;
function firstTabdragStart(args: DragEventArgs) {
    firstTabitem = [firstTabObj.items[args.index]];
    args.draggedItem.style.visibility = 'hidden';
    dragItemContainer = <HTMLElement>args.draggedItem.closest('.e-tab');
}
function firstTabDragStop(args: DragEventArgs) {
    if (!isNullOrUndefined(args.target.closest('.e-tab')) && !dragItemContainer.isSameNode(args.target.closest('.e-tab'))) {
        args.cancel = true;
        let TabElement: HTMLElement = <HTMLElement>args.target.closest('.e-tab');
        let dropItem: HTMLElement = <HTMLElement>args.target.closest('.e-toolbar-item');
        if (TabElement != null && dropItem != null) {
            dragItemIndex = Array.prototype.indexOf.call(firstTabObj.element.querySelectorAll('.e-toolbar-item'), args.draggedItem);
            let dropItemContainer: Element = args.target.closest('.e-toolbar-items');
            let dropItemIndex: number = (dropItemContainer != null) ? (Array.prototype.slice.call(dropItemContainer.querySelectorAll('.e-toolbar-item'))).indexOf(dropItem) : '';
            secondTabObj.addTab(firstTabitem, dropItemIndex);
            firstTabObj.removeTab(dragItemIndex);
        }
    }
}
function secondTabDragStart(args: DragEventArgs) {
    secondTabitem = [secondTabObj.items[args.index]];
    args.draggedItem.style.visibility = 'hidden';
    dragItemContainer = <HTMLElement>args.draggedItem.closest('.e-tab');
}
function secondTabDragStop(args: DragEventArgs) {
    if (!isNullOrUndefined(args.target.closest('.e-tab')) && !dragItemContainer.isSameNode(args.target.closest('.e-tab'))) {
        args.cancel = true;
        let TabElement: HTMLElement = <HTMLElement>args.target.closest('.e-tab');
        let dropItem: HTMLElement = <HTMLElement>args.target.closest('.e-toolbar-item');
        if (TabElement != null && dropItem != null) {
            dragItemIndex = Array.prototype.indexOf.call(secondTabObj.element.querySelectorAll('.e-toolbar-item'), args.draggedItem);
            let dropItemContainer: Element = args.target.closest('.e-toolbar-items');
            let dropItemIndex: number = (dropItemContainer != null) ? (Array.prototype.slice.call(dropItemContainer.querySelectorAll('.e-toolbar-item'))).indexOf(dropItem) : '';
            firstTabObj.addTab(secondTabitem, dropItemIndex);
            secondTabObj.removeTab(dragItemIndex);
        }
    }
}

```

{% endtab %}

## Drag and drop items to external source

It is possible to drag and drop the items to any of the external sources from the Tab, by manually saving those dropped items as new node data through the `addNodes` method of Treeview and removing the dragged item through the `removeTab` method of Tab.

In this example, we have used the tree view control as an external source, and the item from the tab component is dragged and dropped onto the child nodes of the tree view component. Therefore, it is necessary to use  the `dragged` event of the Tab component, where we can form an event object and save it using the `addNodes` method of the Treeview and remove the dragged item through the `removeTab` method of Tab using the dragged item index.

{% tab template="tab/drag-and-drop/tab-to-treeview", sourceFiles="index.ts,index.html", es5Template="tab-to-treeview-template" %}

```typescript

import { isNullOrUndefined } from '@syncfusion/ej2-base';
import { Tab, DragEventArgs, TabItemModel } from '@syncfusion/ej2-navigations';
import { TreeView } from '@syncfusion/ej2-navigations';

let tabObj: Tab = new Tab({
    created: onTabCreate,
    heightAdjustMode: 'Auto',
    dragArea: '#container',
    allowDragAndDrop: true,
    dragged: tabDragStop,
    items: [
        {
            header: { 'text': 'India' },
            content: 'India officially the Republic of India, is a country in South Asia. It is the seventh-largest country by area, the second-most populous country with over 1.2 billion people, and the most populous democracy in the world. Bounded by the Indian Ocean on the south, the Arabian Sea on the south-west, and the Bay of Bengal on the south-east, it shares land borders with Pakistan to the west;China, Nepal, and Bhutan to the north-east; and Burma and Bangladesh to the east. In the Indian Ocean, India is in the vicinity of Sri Lanka and the Maldives; in addition, India Andaman and Nicobar Islands share a maritime border with Thailand and Indonesia.'
        },
        {
            header: { 'text': 'Australia' },
            content: 'Australia, officially the Commonwealth of Australia, is a country comprising the mainland of the Australian continent, the island of Tasmania and numerous smaller islands. It is the world sixth-largest country by total area. Neighboring countries include Indonesia, East Timor and Papua New Guinea to the north; the Solomon Islands, Vanuatu and New Caledonia to the north-east; and New Zealand to the south-east.'
        },
        {
            header: { 'text': 'USA' },
            content: 'The United States of America (USA or U.S.A.), commonly called the United States (US or U.S.) and America, is a federal republic consisting of fifty states and a federal district. The 48 contiguous states and the federal district of Washington, D.C. are in central North America between Canada and Mexico. The state of Alaska is west of Canada and east of Russia across the Bering Strait, and the state of Hawaii is in the mid-North Pacific. The country also has five populated and nine unpopulated territories in the Pacific and the Caribbean.'
        },
        {
            header: { 'text': 'France' },
            content: 'France, officially the French Republic is a sovereign state comprising territory in western Europe and several overseas regions and territories. The European part of France, called Metropolitan France, extends from the Mediterranean Sea to the English Channel and the North Sea, and from the Rhine to the Atlantic Ocean; France covers 640,679 square kilo metres and as of August 2015 has a population of 67 million, counting all the overseas departments and territories.'
        }
    ],
});
tabObj.appendTo('#draggableTab');

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
    cssClass: 'treeview-external-drop-tab'
});

treeViewInstance.appendTo('#draggableTreeview');
let i: number = 0;

function onTabCreate(): void {
    let tabElement: HTMLElement = document.getElementById('draggableTab');
    if (!isNullOrUndefined(tabElement)) {
        tabElement.querySelector('.e-tab-header').classList.add('e-droppable');
        tabElement.querySelector('.e-content').classList.add('tab-content');
    }
}

function tabDragStop(args: DragEventArgs) {
    let dragTabIndex: number = Array.prototype.indexOf.call(tabObj.element.querySelectorAll('.e-toolbar-item'), args.draggedItem);
    let dragItem: TabItemModel = tabObj.items[dragTabIndex];
    let dropNode: HTMLElement = <HTMLElement>args.target.closest('#draggableTreeview .e-list-item');
    if (dropNode != null && !args.target.closest('#draggableTab .e-toolbar-item')) {
        args.cancel = true;
        let dropContainer: NodeListOf<Element> = (document.querySelector('.treeview-external-drop-tab')).querySelectorAll('.e-list-item');
        let dropIndex: number = Array.prototype.indexOf.call(dropContainer, dropNode);
        let newNode: { [key: string]: Object }[] = [{ id: 'list' + i, text: dragItem.header.text  }];
        tabObj.removeTab(dragTabIndex);
        treeViewInstance.addNodes(newNode, 'Treeview' , dropIndex);
    }
}

```

{% endtab %}

## Drag and drop items from external source

It is possible to drag and drop the items from any of the external sources into the Tab, by manually saving those dropped items as new item data through the `addTab` method of Tab and removing the dragged node through the `removeNodes` method of Treeview.

In this example, we have used the tree view control as an external source, and the child nodes from the tree view component are dragged and dropped onto the Tab. Therefore, it is necessary to use the `nodeDragStop` event of the Treeview component, where we can form an event object and save it using the `addTab` method of the Tab and remove the dragged node through the `removeNodes` method of Treeview.

{% tab template="tab/drag-and-drop/treeview-to-tab", sourceFiles="index.ts,index.html", es5Template="treeview-to-tab-template" %}

```typescript

import { isNullOrUndefined } from '@syncfusion/ej2-base';
import { Tab, TabItemModel } from '@syncfusion/ej2-navigations';
import { TreeView, DragAndDropEventArgs } from '@syncfusion/ej2-navigations';

let tabObj: Tab = new Tab({
    heightAdjustMode: 'Auto',
    dragArea: '#container',
    items: [
        {
            header: { 'text': 'India' },
            content: 'India officially the Republic of India, is a country in South Asia. It is the seventh-largest country by area, the second-most populous country with over 1.2 billion people, and the most populous democracy in the world. Bounded by the Indian Ocean on the south, the Arabian Sea on the south-west, and the Bay of Bengal on the south-east, it shares land borders with Pakistan to the west;China, Nepal, and Bhutan to the north-east; and Burma and Bangladesh to the east. In the Indian Ocean, India is in the vicinity of Sri Lanka and the Maldives; in addition, India Andaman and Nicobar Islands share a maritime border with Thailand and Indonesia.'
        },
        {
            header: { 'text': 'Australia' },
            content: 'Australia, officially the Commonwealth of Australia, is a country comprising the mainland of the Australian continent, the island of Tasmania and numerous smaller islands. It is the world sixth-largest country by total area. Neighboring countries include Indonesia, East Timor and Papua New Guinea to the north; the Solomon Islands, Vanuatu and New Caledonia to the north-east; and New Zealand to the south-east.'
        },
        {
            header: { 'text': 'USA' },
            content: 'The United States of America (USA or U.S.A.), commonly called the United States (US or U.S.) and America, is a federal republic consisting of fifty states and a federal district. The 48 contiguous states and the federal district of Washington, D.C. are in central North America between Canada and Mexico. The state of Alaska is west of Canada and east of Russia across the Bering Strait, and the state of Hawaii is in the mid-North Pacific. The country also has five populated and nine unpopulated territories in the Pacific and the Caribbean.'
        },
        {
            header: { 'text': 'France' },
            content: 'France, officially the French Republic is a sovereign state comprising territory in western Europe and several overseas regions and territories. The European part of France, called Metropolitan France, extends from the Mediterranean Sea to the English Channel and the North Sea, and from the Rhine to the Atlantic Ocean; France covers 640,679 square kilo metres and as of August 2015 has a population of 67 million, counting all the overseas departments and territories.'
        }
    ],
});
tabObj.appendTo('#draggableTab');

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
let treeViewObj: TreeView = new TreeView({
    fields: { dataSource: data, id: 'id', text: 'text' },
    allowDragAndDrop: true,
    dragArea: '#container',
    nodeDragStop: onNodeDragStop,
    nodeDragging: onNodeDrag,
    cssClass: 'treeview-external-drop-tab'
});
treeViewObj.appendTo('#draggableTreeview');

function onNodeDragStop(args: DragAndDropEventArgs): void {
    let dropElement: HTMLElement = <HTMLElement>args.target.closest('#draggableTab .e-toolbar-item');
    if (dropElement != null) {
        let tabElement: HTMLElement = document.querySelector('#draggableTab');
        let dropItemIndex: number = [].slice.call(tabElement.querySelectorAll('.e-toolbar-item')).indexOf(dropElement);
        let newTabItem: TabItemModel[] = [{
            header: { 'text': args.draggedNodeData.text.toString() },
            content: args.draggedNodeData.text.toString() + ' Content'
        }];
        tabObj.addTab(newTabItem, dropItemIndex);
        treeViewObj.removeNodes([args.draggedNode]);
        args.cancel = true;
    } else {
        let dropNode: HTMLElement = <HTMLElement>args.target.closest('#draggableTreeview .e-list-item ');
        if (!isNullOrUndefined(dropNode) && args.dropIndicator === 'e-drop-in') {
            args.cancel = true;
        }
    }
}
function onNodeDrag(args: DragAndDropEventArgs): void {
    if (!isNullOrUndefined(args.target.closest('.tab-content'))) {
        args.dropIndicator = 'e-no-drop';
    } else if (!isNullOrUndefined(args.target.closest('#draggableTab .e-tab-header'))) {
        args.dropIndicator = 'e-drop-in';
    }
}

```

{% endtab %}