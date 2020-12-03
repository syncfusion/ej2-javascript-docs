---
title: "ListView How to display spinner for list item loading from remote data"
component: "ListView"
description: "ListView how to section, get selected item, dual list, listview filtering, add & remove items from listview, grid layout using listview, listview drag & drop."
---

# How to display spinner for list item loading from remote data

The features of the ListView control such as remote data-binding take more time to fetch data from corresponding
dataSource/remote URL. In this case, you can use EJ2
[Spinner](../../spinner/) to enhance the appearance of the UI. This
section explains how to load a spinner control to groom the appearance.

Refer to the following code sample to render the spinner control.

```typescript
    createSpinner({
        target: document.getElementById('spinner')
    });
    showSpinner(document.getElementById('spinner'));
```

Refer to the following code sample to render the ListView control.

```typescript

let listviewInstance: ListView = new ListView({
    //Bind the DataManager instance to the dataSource property
    dataSource: new DataManager({
        url: '//js.syncfusion.com/ejServices/Wcf/Northwind.svc/',
        crossDomain: true
    }),

    //Bind the Query instance to the query property
    query: new Query().from('Products').select('ProductID,ProductName').take(10),

    //Map the appropriate columns to the fields property
    fields: { id: 'ProductID', text: 'ProductName' },

    //Set the header tittle to the list
    headerTitle: 'Product Name',
    showHeader: true,
    width:"300",
    actionComplete  : oncomplete
});

//Render the initialized ListView
listviewInstance.appendTo("#element");
```

Here, the data is fetched from `Northwind` Service URL; it takes a few seconds to load the data. To enhance the UI, the
spinner control has been rendered initially. After the data is loaded from remote URL, the spinner control will be
hidden in ListView
[actionComplete](../../api/list-view#actioncomplete)
event.

{% tab template="listview/spinner", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css", es5Template="spinner-template" %}

```typescript

import { ListView } from '@syncfusion/ej2-lists';
//Import DataManager related classes
import { DataManager, Query } from '@syncfusion/ej2-data';
import { createSpinner, showSpinner } from '@syncfusion/ej2-popups';

//Initialize the ListView control
let listviewInstance: ListView = new ListView({
    //Bind the DataManager instance to the dataSource property
    dataSource: new DataManager({
        url: '//js.syncfusion.com/ejServices/Wcf/Northwind.svc/',
        crossDomain: true
    }),

    //Bind the Query instance to the query property
    query: new Query().from('Products').select('ProductID,ProductName').take(10),

    //Map the appropriate columns to the fields property
    fields: { id: 'ProductID', text: 'ProductName' },

    //Set the header tittle to the list
    headerTitle: 'Product Name',
    showHeader: true,
    width:"300",
    actionComplete  : oncomplete
});

//Render the initialized ListView
listviewInstance.appendTo("#element");

createSpinner({
        target: document.getElementById('spinner')
    });
    showSpinner(document.getElementById('spinner'));

function oncomplete(){
  document.getElementById('spinner').style.display = "none";
}

```

{% endtab %}
