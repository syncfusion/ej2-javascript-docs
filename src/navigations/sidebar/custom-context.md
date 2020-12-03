---
title: "Custom Context"
component: "Sidebar"
description: "Sidebar can set to be initialized , target to any HTML element alongside of the main content of a web page."
---

# Target

Sidebar has a flexible option to make it initialize, target to any HTML element alongside of the main content of a web page.

By default, Sidebar initializes target to the body element. Using the [`target`](../api/sidebar/#target) property, set target element to initialize the Sidebar inside any HTML element apart from the body element.

> If required , `zIndex` can be set when sidebar act as overlay type.

In the following sample, sidebar is rendered context to a div container element which has the CSS class `e-main-content`.

{% tab template="sidebar/context", es5Template="es5_sidebar_target" ,isDefaultActive=true, sourceFiles="app.ts,index.html,styles.css"%}

```typescript
import { Sidebar } from '@syncfusion/ej2-navigations';
import { Button } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

let defaultSidebar: Sidebar = new Sidebar({
    width: "280px",
    type: "Push",
    target: '.maincontent'
});
defaultSidebar.appendTo('#default-sidebar');
//end of Sidebar initialization

//toggle button initialization
let togglebtn: Button = new Button({iconCss: 'e-icons burg-icon', isToggle: true, content:'Open'}, '#toggle');

// Close the Sidebar
document.getElementById('close').onclick = (): void => {
    defaultSidebar.hide();
    document.getElementById('toggle').classList.remove('e-active');
    togglebtn.content = 'Open'
};

//Click Event.
document.getElementById('toggle').onclick = (): void => {
        if (document.getElementById('toggle').classList.contains('e-active')) {
            togglebtn.content = 'Close';
            defaultSidebar.show();
        } else {
            togglebtn.content = 'Open';
            defaultSidebar.hide();
        }
    };
```

{% endtab %}