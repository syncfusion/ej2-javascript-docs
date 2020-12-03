---
title: "Syncfusion JavaScript ListView Customizing Templates"
component: "ListView"
description: "Learn about JavaScript listview control customization of list item, header, and category group header using template and group header properties."
---

# Customizing templates

The ListView control is designed to customize list items, group title and header title. It uses Essential JS2 [Template engine](../common/template-engine/) to render the elements.

## Header template

ListView header can be customized with the help of the [`headerTemplate`](../api/list-view/#headertemplate) property.

To customize header template in your application, set your customized template string to `headerTemplate` property along with [`showHeader`](../api/list-view/#showheader) property as `true` to display the ListView header.

```typescript

let listviewInstance: ListView = new ListView({
     data: listData,
     headerTemplate: '<div class="header-content"><span>Header</span></div>',
     showHeader: true
})

```

In the following example, we have rendered Listview with customized header which contains search, add and sort buttons.

{% tab template="listview/header-template", isDefaultActive = "true", sourceFiles="index.ts,index.html,index.css", es5Template="header-template"  %}

```typescript

import { ListView } from '@syncfusion/ej2-lists';
import { Button } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

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

let listViewInstance: any = new ListView({
    dataSource: fruitsdata,
    headerTemplate: '<div class="headerContainer"><span class="fruitHeader">Fruits</span><button id="search"></button><button id="add"></button><button id="sort"></button></div>',
    showHeader: true,
    actionComplete: renderHeaderButtons
});

listViewInstance.appendTo('#element');

function renderHeaderButtons() {
    ['search', 'sort', 'add'].forEach((item: string) => {
        new Button({ iconCss: `e-icons e-${item}-icon`, cssClass: 'e-small e-round', isPrimary: true }, `#${item}`)
    });
}

```

{% endtab %}

## Template

ListView items can be customized with the help of the [`template`](../api/list-view/#template) property.

To customize list items in your application, set your customized template string to `template` property.

```typescript

let listviewInstance: ListView = new ListView({
     data: listData,
     template: '<div class="list-tem"><span>${text}</span></div>',
})

```

We provided the following built-in CSS classes to customize the list-items. Refer to the following table.

| CSS class        | Description           |
| ------------- |-------------|
| e-list-template, e-list-wrapper | These classes are used to differentiate normal and template rendering, which are mandatory for template rendering. The `e-list-template` class should be added to the root of the ListView element and `e-list-wrapper` class should be added to the template element wrapper <br/><br/> `new ListView({` <br/> `dataSource: data,` <br/> <b>`cssClass: 'e-list-template',`</b> <br/> `template: '<div class="`<b>`e-list-wrapper`</b>`"></div>'}, '#list');`
| e-list-content | This class is used to align list content and it should be added to the content element <br/><br/> `<div class="e-list-wrapper">`<br/><b>`<span class="e-list-content">ListItem</span>`</b> <br/>`</div>`|
| e-list-avatar | This class is used for avatar customization. It should be added to the template element wrapper. After adding it, we can customize our element with [Avatar](../avatar/getting-started/) classes <br/><br/> `<div class="e-list-wrapper`<b>`e-list-avatar`</b>`">` <br/> <b>`<span class="e-avatar e-avatar-circle">MR</span>`</b><br/>`<span class="e-list-content">ListItem</span>`<br/>`</div>`|
| e-list-avatar-right | This class is used to align avatar to right side of the list item. It should be added to the template element wrapper. After adding it, we can customize our element with [Avatar](../avatar/getting-started/) classes <br/><br/> `<div class="e-list-wrapper`<b>`e-list-avatar-right`</b>`">` <br/> `<span class="e-list-content">ListItem</span>`<br/><b>`<span class="e-avatar e-avatar-circle">MR</span>`</b><br/> `</div>`|
| e-list-badge | This class is used for badge customization .It should be added to the template element wrapper. After adding it, we can customize our element with [Badge](../badge/getting-started/) classes <br/><br/> `<div class="e-list-wrapper`<b>`e-list-badge`</b>`">` <br/> `<span class="e-list-content">ListItem</span>`<br/><b>`<span class="e-badge e-badge-primary">MR</span>`</b><br/> `</div>`|
| e-list-multi-line | This class is used for multi-line customization. It should be added to the template element wrapper. After adding it, we can customize List item's header and description <br/><br/>`<div class="e-list-wrapper`<b>`e-list-multi-line`</b>`">` <br/> `<span class="e-list-content">ListItem</span>`<br/>`</div>`|
| e-list-item-header |This class is used to align a list header and it should be added to the header element along with the multi-line class <br/><br/> `<div class="e-list-wrapper`<b>`e-list-multi-line`</b>`">`<br/> <b>`<span class="e-list-item-header">ListItem Header</span>`</b><br/> `<span class="e-list-content">ListItem</span>`<br/>`</div>`|

In the following example, we have customized list items with built-in CSS classes.

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
let dataSource: any = [
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

## Group template

ListView group header can be customized with the help of the [`groupTemplate`](../api/list-view/#grouptemplate) property.

To customize the group template in your application, set your customized template string to `groupTemplate` property.

```typescript

let listviewInstance: ListView = new ListView({
     data: listData,
     groupTemplate: '<div class="group-header"><span>${items[0].category}</span></div>',
})

```

In the following example, we have grouped Listview based on the category. The category of each list item should be mapped with [`groupBy`](../api/list-view/fieldSettingsModel/#groupby) field of the data. We have also displayed grouped list items count in the group list header.

{% tab template="listview/item-count", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css", es5Template="item-template" %}

```typescript

import { ListView } from '@syncfusion/ej2-lists';

    let template: string = '<div class="e-list-wrapper e-list-multi-line e-list-avatar">' +
    '<img class="e-avatar e-avatar-circle" src=${image} style="background:#BCBCBC" />' +
    '<span class="e-list-item-header">${Name}</span>' +
    '<span class="e-list-content">${contact}</span>' +
    '</div>';

    //Define an array of JSON data
    let dataSource = [
        { Name: 'Nancy', contact:'(206) 555-985774', id: '1', image: 'https://ej2.syncfusion.com/demos/src/grid/images/1.png',  category: 'Experience'},
        { Name: 'Janet', contact: '(206) 555-3412', id: '2', image: 'https://ej2.syncfusion.com/demos/src/grid/images/3.png', category: 'Fresher' },
        { Name: 'Margaret', contact:'(206) 555-8122', id:'4', image: 'https://ej2.syncfusion.com/demos/src/grid/images/4.png', category: 'Experience' },
        { Name: 'Andrew ', contact:'(206) 555-9482', id: '5', image: 'https://ej2.syncfusion.com/demos/src/grid/images/2.png' category: 'Experience'},
        { Name: 'Steven', contact:'(71) 555-4848', id: '6', image: 'https://ej2.syncfusion.com/demos/src/grid/images/5.png', category: 'Fresher' },
        { Name: 'Michael', contact:'(71) 555-7773', id: '7', image: 'https://ej2.syncfusion.com/demos/src/grid/images/6.png', category: 'Experience' },
        { Name: 'Robert', contact:'(71) 555-5598', id: '8', image: 'https://ej2.syncfusion.com/demos/src/grid/images/7.png', category: 'Fresher' },
        { Name: 'Laura', contact:'(206) 555-1189', id: '9', image: 'https://ej2.syncfusion.com/demos/src/grid/images/8.png', category: 'Experience' },
    ];

    // Initialize the ListView control
    let listObj: ListView = new ListView({

        //Set the defined data to the data source property
        dataSource: dataSource,

        width: 350,

        //Map the appropriate columns to the fields property
        fields: { text: 'Name', groupBy: 'category' },

        //set cssClass for template customization
        cssClass: 'e-list-template',

        //Set the customized template
        template: template,
        groupTemplate: '<div><span class="category">${items[0].category}</span> <span class="count"> ${items.length} Item(s)</span></div> '

    });

    //Render the initialized ListView control
    listObj.appendTo('#List');

```

{% endtab %}

> We can also render other EJ2 controls in ListView templates by rendering that controls on [`actionComplete`](../api/list-view/#actioncomplete) event. Refer to the below code snippet.

```typescript

let listviewInstance: ListView = new ListView({
     data: listData,
     template: '<div><span>${text}</span><button id="delete"></button></div>',
     actionComplete: () => {
         new Button({iconCss: 'e-icons e-delete-icon' cssClass: 'e-small e-round', isPrimary: true }, '#delete')
     }
})

```