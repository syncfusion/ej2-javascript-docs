---
title: "Syncfusion JavaScript ListView (UI)Virtualization"
component: "ListView"
description: "Learn about JavaScript listview control virtualization, loads viewable items in view port, which improves listview performance when loading large data."
---

# UI Virtualization

UI virtualization loads only viewable list items in a view port, which will improve the ListView performance while loading a large number of data.

## Module injection

To use UI virtualization, you should import `virtualization` module from the `ej2-lists` package and inject it using `ListView.Inject()`
method as shown in the following code snippet.

```typescript

import { ListView, Virtualization } from '@syncfusion/ej2-lists';

ListView.Inject(Virtualization);

```

## Getting started

UI virtualization can be enabled in the ListView by setting the
[`enableVirtualization`](../api/list-view#enablevirtualization)
property to true.

It has two types of scrollers as follows:

**Window scroll**: This scroller is used in the ListView by default.

**Container scroll**: This scroller is used, when the height property of the ListView is set.

{% tab template="listview/virtualization/flat-list", isDefaultActive = "true", sourceFiles="index.ts,index.html",es5Template="flat-list-template" %}

```typescript

import { ListView, Virtualization } from '@syncfusion/ej2-lists';

ListView.Inject(Virtualization);

let listData: { [key: string]: string | object }[] = [];

listData = [
    { text: 'Nancy', id: '0', },
    { text: 'Andrew', id: '1' },
    { text: 'Janet', id: '2' },
    { text: 'Margaret', id: '3' },
    { text: 'Steven', id: '4' },
    { text: 'Laura', id: '5' },
    { text: 'Robert', id: '6' },
    { text: 'Michael', id: '7' },
    { text: 'Albert', id: '8' },
    { text: 'Nolan', id: '9' }
];

for (let i: number = 10; i <= 1010; i++) {
    let index: number = parseInt((Math.random() * 10).toString());
    listData.push({ text: listData[index].text, id: i.toString() });
}

let listObj: ListView = new ListView({

    //Set defined data to dataSource property.
    dataSource: listData,
    //Set height
    height: 500,
    //enable UI virtualization
    enableVirtualization: true,
});

listObj.appendTo('#ui-list');

```

{% endtab %}

You can use the `template` property to customize list items in UI virtualization.

{% tab template="listview/virtualization/template", isDefaultActive = "true", sourceFiles="index.ts,index.html",es5Template="virtual-template" %}

```typescript

import { ListView, Virtualization } from '@syncfusion/ej2-lists';

ListView.Inject(Virtualization);

let listData: { [key: string]: string | object }[] = [];
listData = [
    { name: 'Nancy', icon: 'N', id: '0', },
    { name: 'Andrew', icon: 'A', id: '1' },
    { name: 'Janet', icon: 'J', id: '2' },
    { name: 'Margaret', imgUrl: './margaret.png', id: '3' },
    { name: 'Steven', icon: 'S', id: '4' },
    { name: 'Laura', imgUrl: './laura.png', id: '5' },
    { name: 'Robert', icon: 'R', id: '6' },
    { name: 'Michael', icon: 'M', id: '7' },
    { name: 'Albert', imgUrl: './albert.png', id: '8' },
    { name: 'Nolan', icon: 'N', id: '9' }
];

for (let i: number = 10; i <= 1010; i++) {
    let index: number = parseInt((Math.random() * 10).toString());
    listData.push({ name: listData[index].name, icon: listData[index].icon, imgUrl: listData[index].imgUrl, id: i.toString() });
}

let listObj: ListView = new ListView({

    //Set defined data to dataSource property.
    dataSource: listData,

    //enable UI virtualization
    enableVirtualization: true,

    //Set height
    height: 500,

    //Set header title
    headerTitle: 'Contacts',

    //Set true to show header title
    showHeader: true,

    //Set defined customized template
    template: '<div class="list-container"><div id="icon" class="${$imgUrl ? \'img\' : $icon }"><span class="${$imgUrl ? \'hideUI\' : \'showUI\' }"> ${icon}</span> <img class="${$imgUrl ? \'showUI\' : \'hideUI\' }" width = 45 height = 45 src="${$imgUrl ?  $imgUrl : \' \' }" /></div><div class="name">${name}</div></div>'

});

listObj.appendTo('#ui-list');

```

{% endtab %}

## Conditional rendering

The following conditional rendering support is provided for the template and groupTemplate.

| Name | Syntax |
| --- | --- | --- |
| conditional class | `<div class="${ $id % 2 === 0 ? 'even-list' : 'odd-list'}"></div>`  |
| conditional attribute | `<div id="${ $id % 2 === 0 ? 'even-list' : 'odd-list'}"></div>`  |
| conditional text content | `<div>${ $id % 2 === 0 ? 'even-list' : 'odd-list'}</div>`  |

In the following sample, the light blue is applied for the even list and light coral is applied for the odd list based on the conditional class.

{% tab template="listview/virtualization/conditional-ui", isDefaultActive = "true", sourceFiles="index.ts,index.html",es5Template="list-template" %}

```typescript

import { ListView, Virtualization } from '@syncfusion/ej2-lists';

ListView.Inject(Virtualization);

let listData: { [key: string]: string | object }[] = [];

listData = [
    { text: 'Nancy', id: '0', },
    { text: 'Andrew', id: '1' },
    { text: 'Janet', id: '2' },
    { text: 'Margaret', id: '3' },
    { text: 'Steven', id: '4' },
    { text: 'Laura', id: '5' },
    { text: 'Robert', id: '6' },
    { text: 'Michael', id: '7' },
    { text: 'Albert', id: '8' },
    { text: 'Nolan', id: '9' }
];

for (let i: number = 10; i <= 1010; i++) {
    let index: number = parseInt((Math.random() * 10).toString());
    listData.push({ text: listData[index].text, id: i.toString() });
}

let listObj: ListView = new ListView({

    //Set defined data to dataSource property.
    dataSource: listData,

    //enable UI virtualization
    enableVirtualization: true,

    //Set height
    height: 500,

    //Set defined customized template
    template: '<div id="list-container" class="${ $id % 2 === 0 ? \'even-list\' : \'odd-list\' }" > ${text} </div>'
});

listObj.appendTo('#ui-list');

```

{% endtab %}