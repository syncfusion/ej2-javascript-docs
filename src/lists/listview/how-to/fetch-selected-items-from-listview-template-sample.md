---
title: "ListView how to fetch selected items from listview template sample"
component: "ListView"
description: "ListView how to section, get selected item, dual list, listview filtering, add & remove items from listview, grid layout using listview, listview drag & drop."
---

# How To fetch selected items from listview template sample

Single or multiple items can be selected by users in the ListView control.

By default, dataSource id and text is mapped in default rendering of listview, since it returns the selected item data properly. But in the custom template, dataSource and the corresponding mapping (text, id, elements rendered inside li element) will vary as per the application requirement.

So, we need to map id attribute to listview items using [fields](../../api/list-view#fields) of [dataSource](../../api/list-view#datasource) to get the selected item data properly while working with custom templates. Refer to the below code snippet for template sample.

```typescript

// Initialize ListView control
 let listObj: ListView = new ListView({

    //Set defined data to dataSource property
    dataSource: dataSource,

    //Map the appropriate columns to fields property
    fields: { text: 'Name', id:'Name'},

    //Set customized template
    template: template,

    enableRtl: true,

    //ListView Select event
    select: onSelect

});

//Render initialized ListView control
listObj.appendTo('#listview');


```

{% tab template="listview/listview-template", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css", es5Template="list-template" %}

```typescript

import { ListView } from '@syncfusion/ej2-lists';

    let template: any = '<div class="settings">'
        + '<div id="postContainer"><div id="postImg">'
        + '<img src=${image} style="height:35px;width:35px;border-radius:50%; border: 1px solid #ccc;" /></div>'
        + '<div id="content">'
        + '<div class="name">${Name}</div>'
        + '<div id="info">${contact}</div>'
        + '</div>'
        + '</div>'

    //Define an array of JSON data
    let dataSource: any = [
    { Name: 'Nancy', contact: '(206) 555-985774', id: '1', image: 'https://ej2.syncfusion.com/demos/src/grid/images/1.png', category: 'Experience' },
    { Name: 'Janet', contact: '(206) 555-3412', id: '2', image: 'https://ej2.syncfusion.com/demos/src/grid/images/3.png', category: 'Fresher' },
    { Name: 'Margaret', contact: '(206) 555-8122', id: '4', image: 'https://ej2.syncfusion.com/demos/src/grid/images/4.png', category: 'Experience' },
    { Name: 'Andrew ', contact: '(206) 555-9482', id: '5', image: 'https://ej2.syncfusion.com/demos/src/grid/images/2.png', category: 'Experience' },
    { Name: 'Steven', contact: '(71) 555-4848', id: '6', image: 'https://ej2.syncfusion.com/demos/src/grid/images/5.png', category: 'Fresher' },    ];

    // Initialize ListView control
    let listObj: ListView = new ListView({

        //Set defined data to dataSource property
        dataSource: dataSource,

        //Map the appropriate columns to fields property
        fields: { text: 'Name', id:'Name'},

        //Set customized template
        template: template,

        enableRtl: true,
        select: onSelect

    });

    //Render initialized ListView control
    listObj.appendTo('#listview');

   function onSelect(){
    let selectedItem = listObj.getSelectedItems();
    document.getElementById('val').innerHTML = 'Selected Item : <b>'+selectedItem.text+'</b>';
   }

```

{% endtab %}
