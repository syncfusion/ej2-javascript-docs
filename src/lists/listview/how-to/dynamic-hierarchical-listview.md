---
title: "ListView how to dynamic hierarchical listview"
component: "ListView"
description: "ListView how to section, get selected item, dual list, listview filtering, add & remove items from listview, grid layout using listview, listview drag & drop."
---

# How to dynamic hierarchical listview

To dynamic hierarchical listview, push the new list item data into the existing
[`dataSource`](../../api/list-view#datasource) using
the [`select`](../../api/list-view#select) event.

Refer to the following steps to load list item into the child list:

1. Initially, render the ListView with the required data source.

2. Bind the [`select`](../../api/list-view#select) event that
triggers selecting list item in the ListView control. By using the select event, you can push the new list item to the child
list of the data source on specifying its item index. Item index can be obtained from the
[`SelectEventArgs`](../../api/list-view/selectEventArgs/) of the
select event.

{% tab template="listview/child-list", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css", es5Template="childList-template" %}

```typescript

import { ListView, SelectEventArgs } from '@syncfusion/ej2-lists';

let dataSource: { [key: string]: Object }[] = [
    {
        id: '01', text: 'Music', icon: 'folder',
        child: [
            { id: '01-01', text: 'Gouttes.mp3', icon: 'file' }
        ]
    },
    {
        id: '02', text: 'Videos', icon: 'folder',
        child: [
            { id: '02-01', text: 'Naturals.mp4', icon: 'file' },
            { id: '02-02', text: 'Wild.mpeg', icon: 'file' },
        ]
    },
    {
        id: '03', text: 'Documents', icon: 'folder',
        child: [
            { id: '03-01', text: 'Environment Pollution.docx', icon: 'file' },
            { id: '03-02', text: 'Global Water, Sanitation, & Hygiene.docx', icon: 'file' },
            { id: '03-03', text: 'Global Warming.ppt', icon: 'file' },
            { id: '03-04', text: 'Social Network.pdf', icon: 'file' },
            { id: '03-05', text: 'Youth Empowerment.pdf', icon: 'file' },
        ]
    },
    {
        id: '04', text: 'Pictures', icon: 'folder',
        child: [
            {
                id: '04-01', text: 'Camera Roll', icon: 'folder',
                child: [
                    { id: '04-01-01', text: 'WIN_20160726_094117.JPG', icon: 'file' },
                    { id: '04-01-02', text: 'WIN_20160726_094118.JPG', icon: 'file' },
                    { id: '04-01-03', text: 'WIN_20160726_094119.JPG', icon: 'file' }
                ]
            },
            {
                id: '04-02', text: 'Wind.jpg', icon: 'file'
            },
            {
                id: '04-02', text: 'Stone.jpg', icon: 'file'
            },
            {
                id: '04-02', text: 'Home.jpg', icon: 'file'
            },
            {
                id: '04-02', text: 'Bridge.png', icon: 'file'
            }
        ]
    },
    {
        id: '05', text: 'Downloads', icon: 'folder',
        child: [
            { id: '05-01', text: 'UI-Guide.pdf', icon: 'file' },
            { id: '05-02', text: 'Tutorials.zip', icon: 'file' },
            { id: '05-03', text: 'Game.exe', icon: 'file' },
            { id: '05-04', text: 'TypeScript.7z', icon: 'file' },
        ]
    },
];
//Initialize the listview control
let listviewInstance: ListView = new ListView({

    //Set the defined data to the dataSource property
    dataSource: dataSource,

    //Map the appropriate columns to the fields property
    fields: { iconCss: 'icon', tooltip: 'text' },

    //Set the showIcon to true
    showIcon: true,

    //Set header title
    headerTitle: 'Folders',

    //Set the showHeader to true
    showHeader: true,

    //Select onSelect event to add new list item in child page
    select: onSelect
});

//Render the initialized ListView
listviewInstance.appendTo("#listview");

//Select event to add new list item in child page
function onSelect(args: SelectEventArgs) {
    //Add new file to the child page of selected list item
    this.dataSource[args.index].child.push({ id: '01-02', text: 'Newly Added File', icon: 'file', htmlAttributes: { role: 'li', class: 'list' } });
}

```

{% endtab %}
