---
title: "Syncfusion JavaScript ListView Data Binding"
component: "ListView"
description: "Learn about JavaScript listview control data binding to display the list of items from the local array/JSON data or server-side data source using DataManager."
---

# Data binding

ListView provides an option to load the data either from local dataSource or remote data services. This can be done through the dataSource property that supports the data type of array or [`DataManager`](../api/data/dataManager/).

ListView supports different kind of data services such as OData, OData V4, and Web API, and data formats like XML, JSON, and, JSONP with the help of DataManager Adaptors.

| Fields | Type | Description |
|------|------|-------------|
| id | string | Specifies ID attribute of list item, mapped in dataSource. |
| text | string | Specifies list item display text field. |
| isChecked | string | Specifies checked status of list item. |
| isVisible | string | Specifies visibility state of list item. |
| enabled | string | Specifies enabled state of list item. |
| iconCss | string | Specifies the icon class of each list item that will be added before to the list item text. |
| child | string | Specifies child dataSource fields. |
| tooltip | string | Specifies tooltip title text field. |
| groupBy | string | Specifies category of each list item. |
| sortBy | string | Specifies sorting field, that is used to sort the listview data. |
| htmlAttributes | string | Specifies list item html attributes field. |

> When complex data bind to ListView, you should map the fields properly. Otherwise, the ListView properties remain as undefined or null.

## Bind to local data

Local data can be represented in two ways, they are as follows:

* Array of simple data.
* Array of JSON data.

### Array of simple data

ListView supports to load the array of primitive data like string and numbers. Here, both value and text field act as same.

{% tab template="listview/data-binding/simple-data", isDefaultActive = "true", sourceFiles="index.ts,index.html", es5Template="simple-data-template" %}

```typescript

import { ListView } from '@syncfusion/ej2-lists';

//define the array of string
let arts: string[] = ["Artwork", "Abstract", "Modern Painting", "Ceramics", "Animation Art", "Oil Painting"];

//Initialize ListView control
let listviewInstance: ListView = new ListView({
    //set the data to datasource property
    dataSource: arts
});

//Render initialized ListView
listviewInstance.appendTo("#element");

```

{% endtab %}

### Array of JSON data

ListView can generate its list items through an array of complex data. To get it work properly, you should map the appropriate columns to the field property.

In the following example, role column is mapped with the text field.

{% tab template="listview/data-binding/array-data", isDefaultActive = "true", sourceFiles="index.ts,index.html", es5Template="array-data-template" %}

```typescript

import { ListView } from '@syncfusion/ej2-lists';

//define the array of JSON
let settings: { [key: string]: Object }[] = [
    {
        'Name': 'Display',
        'id': 'list-01'
    },
    {
        'Name': 'Notification',
        'id': 'list-02'
    },
    {
        'Name': 'Sound',
        'id': 'list-03'
    },
    {
        'Name': 'Apps',
        'id': 'list-04'
    },
    {
        'Name': 'Storage',
        'id': 'list-05'
    },
    {
        'Name': 'Battery',
        'id': 'list-06'
    }
];

//Initialize ListView control
let listviewInstance: ListView = new ListView({
    //set the data to datasource property
    dataSource: settings,

    //map the appropriate columns to fields property
     fields: { text: 'Name', tooltip: 'Name', id:'id'},

    //set the header tittle for the list
    headerTitle: 'Device settings',
    showHeader: true

});

//Render initialized ListView
listviewInstance.appendTo("#element");

```

{% endtab %}

## Bind to remote data

The ListView supports to retrieve the data from remote data services with the help of DataManager control. The Query property allows to fetch data and return it to the ListView from the database.

In the following sample, first 6 products from the Product table of NorthWind data service are displayed.

{% tab template="listview/data-binding/remote-data", isDefaultActive = "true", sourceFiles="index.ts,index.html", es5Template="remote-data-template"%}

```typescript

import { ListView } from '@syncfusion/ej2-lists';
//import DataManager related classes
import { DataManager, Query } from '@syncfusion/ej2-data';

//Initialize ListView control
let listviewInstance: ListView = new ListView({
    //bind the DataManager instance to dataSource property
    dataSource: new DataManager({
        url: '//js.syncfusion.com/ejServices/Wcf/Northwind.svc/',
        crossDomain: true
    }),

    //bind the Query instance to query property
    query: new Query().from('Products').select('ProductID,ProductName').take(6),

    //map the appropriate columns to fields property
    fields: { id: 'ProductID', text: 'ProductName' },

    //set the header tittle for the list
    headerTitle: 'Product Name',
    showHeader: true
});

//Render initialized ListView
listviewInstance.appendTo("#element")

```

{% endtab %}
