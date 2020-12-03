---
title: "ListView how To create mobile contact layout from listview"
component: "ListView"
description: "ListView how to section, get selected item, dual list, listview filtering, add & remove items from listview, grid layout using listview, listview drag & drop."
---

# How to create mobile contact layout from listview

You can customize the ListView using the
[template](../../api/list-view#template) property. Refer
to the following steps to customize ListView as mobile contact view with our `ej2-avatar`.

* Render the ListView with
[dataSource](../../api/list-view#datasource) that has
avatar data. You can set avatar data as either text or class names. Refer to the following codes.

```typescript

let dataSource: { [key: string]: Object }[] = [
  {
    text: "Jenifer", contact: "(206) 555-985774", id: "1", avatar: "", pic: "pic01"
  },
  {
    text: "Amenda", contact: "(206) 555-3412", id: "2", avatar: "A", pic: ""
  }
];

```

* Set `avatar` classes in ListView template to customize contact icon. In the following codes, medium size avatar has been
set using the class name `e-avatar e-avatar-circle` from data source.

```typescript

  template: '<div class="e-list-wrapper e-list-multi-line e-list-avatar">' +
    '${if(avatar!=="")}' +
    '<span class="e-avatar e-avatar-circle">${avatar}</span>' +
    '${else}' +
    '<span class="${pic} e-avatar e-avatar-circle"> </span>' +
    '${/if}' +
    '<span class="e-list-item-header">${text}</span>' +
    '<span class="e-list-content">${contact}</span>' +
    '</div>';

```

> Avatars can be set in different sizes in avatar classes. To know more about avatar classes, refer to
[Avatar](https://ej2.syncfusion.com/demos/#/material/avatar/default.html).

* Sort the contact names using the
[`sortOder`](../../api/list-view#sortorder) property of ListView.

* Enable the [`showHeader`](../../api/list-view#showheader)
property, and set the
[`headerTitle`](../../api/list-view#headertitle)
as `Contacts`.

{% tab template="listview/avatar", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css", es5Template="avatar-template" %}

```typescript

import { ListView } from "@syncfusion/ej2-lists";

let template: string = '<div class="e-list-wrapper e-list-multi-line e-list-avatar">' +
    '${if(avatar!=="")}' +
    '<span class="e-avatar e-avatar-circle">${avatar}</span>' +
    '${else}' +
    '<span class="${pic} e-avatar e-avatar-circle"> </span>' +
    '${/if}' +
    '<span class="e-list-item-header">${text}</span>' +
    '<span class="e-list-content">${contact}</span>' +
    '</div>';

//Define an array of JSON data
let dataSource: { [key: string]: Object }[] = [
    {
        text: "Jenifer",
        contact: "(206) 555-985774",
        id: "1",
        avatar: "",
        pic: "pic01"
    },
    { text: "Amenda", contact: "(206) 555-3412", id: "2", avatar: "A", pic: "" },
    {
        text: "Isabella",
        contact: "(206) 555-8122",
        id: "4",
        avatar: "",
        pic: "pic02"
    },
    {
        text: "William ",
        contact: "(206) 555-9482",
        id: "5",
        avatar: "W",
        pic: ""
    },
    {
        text: "Jacob",
        contact: "(71) 555-4848",
        id: "6",
        avatar: "",
        pic: "pic04"
    },
    { text: "Matthew", contact: "(71) 555-7773", id: "7", avatar: "M", pic: "" },
    {
        text: "Oliver",
        contact: "(71) 555-5598",
        id: "8",
        avatar: "",
        pic: "pic03"
    },
    {
        text: "Charlotte",
        contact: "(206) 555-1189",
        id: "9",
        avatar: "C",
        pic: ""
    }
];

// Initialize the ListView control
let listObj: ListView = new ListView({
    //Set the defined data to the dataSource property
    dataSource: dataSource,
    //Map the appropriate columns to the fields property
    fields: { text: "text" },
    //Set the width of the ListView
    width: "350px",
    //Enable the header of the ListView
    showHeader: true,
    //Set the header title
    headerTitle: "Contacts",
    //set cssClass for template customization
    cssClass: 'e-list-template',
    //Set the customized template
    template: template,
    sortOrder: "Ascending"
});

//Render the initialized ListView control
listObj.appendTo("#List");

```

{% endtab %}
