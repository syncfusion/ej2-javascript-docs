---
title: "ListView How to dynamic listview by loading AJAX HTML content"
component: "ListView"
description: "ListView how to section, get selected item, dual list, listview filtering, add & remove items from listview, grid layout using listview, listview drag & drop."
---

# How to dynamic listview by loading AJAX HTML content

We can set external `HTML` page content as [`template`](../../api/list-view#template) for our `ListView` control by making use of `AJAX` call.

```typescript

let template: string;
let ajax: Ajax = new Ajax('./template.html', 'GET', false);
ajax.onSuccess = (e: string)=>{
    template = e;
}

ajax.send();

```

In the below sample, we have rendered smartphone settings template from external `HTML` file.

{% tab template="listview/ajax", isDefaultActive = "true", sourceFiles="index.ts,index.html,index.css", es5Template="ajax-template"  %}

```typescript

import { ListView } from '@syncfusion/ej2-lists';
import { Ajax } from '@syncfusion/ej2-base';

let data: { [key: string]: Object }[] = [
    { name: 'Network & Internet', id: '0', description: 'Wi-Fi, mobile, data usage, hotspot' },
    { name: 'Connected devices', id: '1', description: 'Bluetooth, cast, NFC' },
    { name: 'Battery', id: '2', description: '18% -4h 12m left' },
    { name: 'Display', id: '3', description: 'Wallpaper, sleep, font size' },
    { name: 'Sound', id: '4', description: 'Volume, vibration, Do Not Disturb' },
    { name: 'Storage', id: '5', description: '52% used - 15.48 GB free' }
];

let template: string;
let ajax: Ajax = new Ajax('./template.html', 'GET', false);
ajax.onSuccess = (e: string)=>{
    template = e;
}

ajax.send();

let listViewInstance: ListView = new ListView({
    dataSource: data,
    template: template,
    headerTitle: 'Settings',
    showHeader: true,
    fields: {text:'name', id: 'id'}
});

listViewInstance.appendTo('#element');

```

{% endtab %}
