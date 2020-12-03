---
title: "How To"
component: "Sidebar"
description: "Miscellaneous aspects of customizing the sidebar"
---

# Open and close the Sidebar

Opening and closing the Sidebar can be achieved with built-in public methods.

* [`show()`](../../api/sidebar/#show): Method to open the Sidebar.
* [`hide()`](../../api/sidebar/#hide): Method to close the Sidebar.
* [`toggle()`](../../api/sidebar/#toggle): Method to toggle between open and close states of the Sidebar.

In the following sample, toggle method has been used to show or hide the Sidebar on button click.

{% tab template="sidebar/sidebar-default", es5Template="es5_sidebar_nested", sourceFiles="app.ts,index.html,styles.css" %}

```typescript

import { Sidebar } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

//Sidebar initialization
let defaultSidebar: Sidebar = new Sidebar({
    showBackdrop: false,
    open:function(e)
    {
        console.log("Sidebar is opened");
    },
    close: function(e)
    {
       console.log("Sidebar is closed");
    }
});
defaultSidebar.appendTo('#default');
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
