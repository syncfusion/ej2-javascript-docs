---
title: "Load Tab items dynamically"
component: "Tab"
description: "This example demonstrates how to dynamically load or add a tab item in the Essential JS 2 Tab component."
---

# Load Tab items dynamically

Tabs can be added dynamically by passing array of items and index value to the [`addTab`](../../api/tab#addtab) method.

```typescript
    // New tab title and content inputs are fetched and stored in local variable
    let title: string = document.getElementById('tab-title').value;
    let content: string = document.getElementById('tab-content').value;

    // Required tab item object formed by using textbox inputs
    let item: Object =  { header: { text: title }, content: createElement('pre', { innerHTML: content.replace(/\n/g, '<br>\n') }).outerHTML };

    // Item object and the index argument passed into the addTab method to add a new tab
    tabObj.addTab([item], index);
```

In the following demo, you can add the tab content by clicking the **+**.  This **+** icon is added on the tab header using [`iconCss`](../../api/tab/header#iconcss) property.  Enter the new Tab heading and content details in the available text boxes, click 'Add Tab' button to pass the details as an array and here last index is calculated to append the new tab at the end.

{% tab template="tab/dynamic-tab", es5Template="es5_dynamic_tab", sourceFiles="index.ts,index.html" %}

```typescript

import { enableRipple, createElement } from '@syncfusion/ej2-base';
import { Tab, SelectEventArgs } from '@syncfusion/ej2-navigations';

enableRipple(true);

let totalItems: number = 0;

let tabObj: Tab = new Tab({
    selected: tabSelected,
    items: [
        {
            header: { 'text': 'Tab1' },
            content: '#tab1_content'
        },
        {
            header: { 'iconCss': 'e-add-icon' },
            content: '#form-container'
        }
    ]
});
tabObj.appendTo('#element');

let addBtn : HTMLElement[] = document.querySelectorAll(".e-ileft.e-icon");
addBtn[0].setAttribute("title", "Add Tab");

function tabSelected(args: SelectEventArgs): void {
    if (args.selectedIndex === document.querySelectorAll('#element .e-toolbar-item').length - 1) {
        document.getElementById('tab-title').value = '';
        document.getElementById('tab-content').value = '';
    }
}

document.getElementById('btn-add').onclick = (e : Event) => {
    let title: string = document.getElementById('tab-title').value;
    let content: string = document.getElementById('tab-content').value;
    let item: Object =  { header: { text: title }, content: createElement('pre', { innerHTML: content.replace(/\n/g, '<br>\n') }).outerHTML };

    totalItems = document.querySelectorAll('#element .e-toolbar-item').length;
    tabObj.addTab([item], totalItems-1);
};

```

{% endtab %}
