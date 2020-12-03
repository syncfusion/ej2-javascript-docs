---
title: "How To"
component: "Sidebar"
description: "Miscellaneous aspects of customizing the sidebar"
---

# Multiple Sidebar

Two Sidebars can be initialized in a web page with same main content.
Sidebars can be initialized on right side or left side of the main content using [`position`](../../api/sidebar/#position) property.

>The HTML element with class name `e-main-content` will be considered as the main content and both the Sidebars will behave as side content to this main content area of a web page.

{% tab template="sidebar/multiple", es5Template="es5_sidebar_nested", isDefaultActive=true, sourceFiles="app.ts,index.html,styles.css" %}

```typescript

import { Sidebar } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

let leftSidebar: Sidebar = new Sidebar({
   width: "200px",
    type:'Push'

});
leftSidebar.appendTo('#default');
//end of leftSidebar initialization

let rightSidebar: Sidebar = new Sidebar({
   width: "200px",
    position:'Right',
    type:'Push'
 });
rightSidebar.appendTo('#default1');
//end of rightSidebar initialization

// Toggle(Open/Close) the Sidebar1
document.getElementById('toggle-btn').onclick = function () {
    leftSidebar.toggle();
};
// Toggle(Open/Close) the Sidebar2
document.getElementById('toggle-btn2').onclick = function () {
    rightSidebar.toggle();
};

```

{% endtab %}