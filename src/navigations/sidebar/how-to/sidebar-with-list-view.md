---
title: "How To"
component: "Sidebar"
description: "Miscellaneous aspects of customizing the sidebar"
---

# Initialize the Sidebar with ListView

Any HTML element can be placed in the Sidebar content area. Sidebar supports all types of HTML structures like `TreeView`, `ListView`, etc.

In the following example, the Sidebar is rendered with ListView component in its content area.

{% tab template="sidebar/sidebar-list", es5Template="es5_sidebar_list", isDefaultActive=true, sourceFiles="app.ts,index.html,styles.css" %}

```typescript

import { Sidebar } from '@syncfusion/ej2-navigations';
import { ListView } from '@syncfusion/ej2-lists';
import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

// Initialize ListView component
let data: { [key: string]: Object }[] = [
    { text: 'Home', id: 'list-02' },
    { text: 'Offers', id: 'list-03' },
    { text: 'Support', id: 'list-04' },
    { text: 'Logout', id: 'list-06' }
];

let listInstance: ListView = new ListView({
    //Set defined data to dataSource property
    dataSource: data
});

//Render initialized ListView component

listInstance.appendTo('#list');

let defaultSidebar: Sidebar = new Sidebar({
    type: "Over", width: '100%'
});
defaultSidebar.appendTo('#default-sidebar');
//end of Sidebar initialization

// Toggle(Open/Close) the Sidebar
document.getElementById('toggle').onclick = (): void => {
    defaultSidebar.toggle();
};

// Close the Sidebar
document.getElementById('close').onclick = (): void => {
    defaultSidebar.hide();
};

```

{% endtab %}
